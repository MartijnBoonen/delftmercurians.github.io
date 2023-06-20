---
title: "Contact"
ShowToc: false
ShowBreadcrumbs: false
hideMeta: true
ShowRssButtonInSectionTermList: false
summary: "Feel free to send an email to contact@delftmercurians.nl for any questions about the team, partnership enquiries, or other matters."
keywords: ["Delft Mercurians", "RoboCup", "contact", "email"]
---

Feel free to send an email to [contact@delftmercurians.nl](mailto:contact@delftmercurians.nl) or fill in our contact form for any questions about
the team, partnership enquiries, or other matters.

<a href="mailto:contact@delftmercurians.nl" class="social-link">
  <img src="/images/social/email_icon.svg" class="social-icon">
  contact@delftmercurians.nl
</a>

<br>

<a href="https://instagram.com/delftmercurians" class="social-link">
  <img src="/images/social/instagram_icon.svg" class="social-icon">
  @delftmercurians
</a>

<br>

<a href="https://www.linkedin.com/company/delft-mercurians/" class="social-link">
  <img src="/images/social/linkedin_icon.svg" class="social-icon">
  delft-mercurians
</a>

<br>

<a href="https://github.com/delftmercurians" class="social-link">
  <img src="/images/social/github_icon.svg" class="social-icon">
  github.com/delftmercurians
</a>

<div class="social-link">
  <img src="/images/social/map_icon.svg" class="social-icon">
  RSA, Julianalaan 67, 2628BC Delft, The Netherlands
</div>

{{< join-callout >}}

<br>

## Contact form

<div id="success" class="success-notification">
  Thanks for your message ! We will get back to you as soon as possible
</div>

<div class="form-container">
  <form action="https://formsubmit.co/contact@delftmercurians.nl" method="POST">
    <label for="name">Full Name</label><br>
    <input class="form-textbox" type="text" name="name" required><br><br>
    <label for="name">Email</label><br>
    <input class="form-textbox" type="email" name="email" required><br><br>
    <label for="subject">Subject</label><br>
    <input class="form-textbox" type="text" name="subject" required><br><br>
    <label for="message">Message</label><br>
    <textarea class="form-textbox" name="message" required rows="4"></textarea><br><br>
    <input type="hidden" name="_next" value="https://delftmercurians.nl/contact/#success">
    <input type="hidden" name="_subject" value="Contact form response">
    <input type="hidden" name="_captcha" value="false">
    <input type="text" name="_honey" style="display:none">
    <button class="send-button" type="submit">
      <span class="send-button-text">Send</span>
    </button>
  </form>
</div>


<style>
.social-icon {
  height: 30px;
  width: 30px;
  display: inline;
  vertical-align: middle;
}
.social-link {
  box-shadow: none !important;
}

.form-container {
  border: 4px solid #009cdc;
  border-radius: 20px;
  padding: 20px;
}

.form-textbox {
  width: 100%;
  font-size: 16px;
  font-size: max(16px, 1em);
  font-family: inherit;
  padding: 0.25em 0.5em;
  background-color: #eee;
  border-radius: 4px;
  resize: none;
  border: none;
}
.form-textbox:focus {
  background-color: #ddd;
}
body.dark .form-textbox {
  background-color: #444;
  color: #fff;
}
body.dark .form-textbox:focus {
  background-color: #555;
}

.form-checkbox-label {
  font-size: 18px;
  font-weight: 300;
}
.form-checkbox {

}

.send-button {
   background-image: linear-gradient(70deg, #f7931e, #ed1c24);
   color: transparent;
   margin: 5px;
   padding: 5px 20px;
   text-align: center;
   border-radius: 10px;
}
.send-button-text {
  color: white;
}

.success-notification {
  background-color: #009933;
  color: #fff;
  border-radius: 20px;
  padding: 20px;
  margin-bottom: 20px;
}
#success {
  display: none;
}
#success:target{
  display: block;
}
</style>
