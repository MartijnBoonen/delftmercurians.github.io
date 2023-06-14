---
author: "Roma"
title: "Filtering: Kalman and alternatives"
summary: "A technical article that looks at dealing with the noise in the data that we get from the cameras"
date: "2023-06-14"
tags: ["software","technical","filtering"]
ShowToc: false
---

*A particularity of the Robocup Small Size League is that we receive data from a camera positioned above the field, which gives us the position of the ball and robots (using the patterns on the top of these). As such, the robots do not do significant computing, but follow commands from the "server" (the machine that receives information from the cameras). This way, we can nicely isolate low-level and high-level controls: the server just tells robots how to move or where to go, and then the robots follow the provided directions.*


### What is this about?

The raw data about positions that the server receives is, broadly speaking, quite noisy. There is not only Gaussian noise, but also the affine offset noise (the same "true" position different cameras see differently), and some weird outliers. However, judging by available recordings of past matches, these noises can be divided into two categories:

1. Gaussian noise: every observation of the positions has some extremely small Gaussian noise (std=3mm), which can be considered independent between two adjacent observations, thus it can be efficiently filtered.
2. "Transition" noise: noise that occurs when multiple cameras see the same entity simultaneously. This noise looks just like an oscillation: there is a constant, but quite large (order of a few centimeters) changes between two adjacent observations, but, if every two consecutive observations averaged, the effect disappears.

As a result of "filtering" we want to get a precise position estimation, and, in addition, some sort of simple algorithm that would allow for short-term prediction of robots and ball trajectories.


### Solving the problem

The most common approach to deal with Gaussian noise is the Kalman Filter: in addition to being an optimal linear filter (in a sense of minimizing the MSE between the "true" value and the output of the filter), it provides a nice dynamics model, that allows for short term prediction. Thus, seemingly, Kalman Filter is a great solution.

However, sadly, it is not. In practice, we almost completely don't care about the Gaussian noise in our observations: precision of a few millimeters is enough to consider the observed data to be "accurate". The issue lies with the second type of noise, the transition noise. While the Kalman filter is capable of filtering it well enough, it requires much higher process covariances than the filter tuned on the Gaussian noise. And, it becomes extremely complicated to infer the covariances of the process just from the data directly, by using some smart mathematical methods. 

Our solution to this issue is quite simple: export some past recordings of games, and then tune the Kalman filter empirically, based on the data. For this reason, we implemented a simplistic visualization, that allows us to play recordings of past games, and tune the Kalman filter coefficients in real time.

<video src="/videos/software_kalman.mp4" controls="true" autoplay="true" loop="true" muted="true" height="500px"></video>

The parameters of the Kalman filter that can be tuned are covariances for position/velocity/acceleration state estimations. The two different colors correspond to Kalman Filter that assumes constant velocity (thus linear behavior, blue line. We will denote it as K4) and Kalman Filter that assumes constant acceleration (thus is able to predict "curvy trajectories", called K6). Moreover, we show the true trajectory a bit into the future, so that we are able to see whether one or another filtering approach is better for short-term prediction. And there is a bunch of convenient controls for the simulation :)

A person who paid attention might ask about the adequacy of using the constant-acceleration Kalman filter for robots: logically, the robots don't have constant acceleration, and one might think that their behavior is even closer to the constant velocity than to the constant acceleration in most of the cases. However, we decided to use K6 as a way to *not* use the Extended Kalman Filter: if we are trying to describe the "smooth" robot trajectories with the best accuracy, we probably should use some sort of high-order approximation of the model, with Bezier curves or with arcs. Seemingly it should work nicely, but Bezier curves are hard to compute, and both of them require the use of the EKF instead of standard KF (since standard KF can handle only the linear system models). And EKF is well-known to have a bunch of issues, that we just don't really want to bother ourselves with: the most common issue is that variance estimations given by EKF might be so significantly incorrect, that the filter will diverge, which is not the case for standard KF. 

And then, a really nice solution appeared: constant acceleration might be seen not exactly as part of the model, but more as a way to include non-linearity in the trajectories. So, our model will model "curvy" behaviors as parabolas, and not as arcs, but in the limit of the short time period they are the same, and, we care only about short-term predictions. Overall, this is a really nice insight into the Kalman filter model definition. 


### Results

As a result, we get a tuned Kalman filter, that is able to extremely nicely predict future robot behavior in terms of a few hundred milliseconds (sometimes even a second or more!). Also, we show why the commonly used linear Kalman Filter is generally a bad solution for state estimation of the robots.


### But what about the alternatives?

Kalman filter is not the only filtering technique out there: the most frequently used ones are Gaussian Processes and Particle filters.

**Gaussian Processes** are a non-parametric filtering technique: it constructs the function that approximates all the observed points via likelihood maximization, when it simply assumes that every point is sampled from the Gaussian distribution, and then tries to maximize likelihood while also being smooth (another Gaussian distribution instead of the model). It is a nice method, but in our case, since the model is quite accurate, it is irrelevant: computation is slow, and the resultant function is less reliable than KF. Moreover, again, the Gaussian component of our observations is usually negligible.

**Particle filters** are a really nice stochastic method to estimate whatever state you have, and it allows you to use non-gaussian likelihoods (so instead of having just a variance of a Gaussian, it uses the actual approximation of the likelihood function). However, it is not really used for this general type of problem, since it requires enormous computing, and is used to handle extreme levels of noise. In fact, the performance of the Particle filters (in comparison to the other approaches) is relative to the noise variance: the larger the variance, the relatively better the particle filter performs. However, the bonus of this method is that it allows us to use absolutely anything as a dynamics model, even neural networks or some other smart (and unstable) techniques, which is really nice. Therefore, we do not completely discard this method: somewhere in the future we might need "mid-term" prediction of robots' behaviors, and then this method will shine.


### To sum up

In the end, we are going to stick with the 6-state (constant acceleration) Kalman Filter. It produces really nice results, and, even though Particle Filter might be better, the computational and implementation-wise overhead does not seem to be worth the change from the standard filtering technique. 
