---
title: "Join the team"
ShowToc: false
ShowBreadcrumbs: false
hideMeta: true
ShowRssButtonInSectionTermList: false
summary: "Want to join the team ? Fill in this application form and we will contact you as soon as possible"
keywords: ["Delft Mercurians", "RoboCup", "join", "apply"]
---

Great that you are interested in joining the Delft Mercurians RoboCup team !

Due to limited space within the team it is important for us to know what positions you would be interested in, so we can do our best to fit everyone in! After filling in the form, we will try to get back to you within the next two weeks.

If you have any questions, you can send an email to [contact@delftmercurians.nl](mailto:contact@delftmercurians.nl)

For more information on the RoboCup SSL league, see [ssl.robocup.org](https://ssl.robocup.org)

Note: All team communication is done in English

<div id="success" class="success-notification">
  Thanks for your application ! We will get back to you as soon as possible
</div>

<div class="form-container">
  <form action="https://formsubmit.co/contact@delftmercurians.nl" method="POST">
    <label for="name">Full Name</label><br>
    <input class="form-textbox" type="text" name="name" required><br><br>
    <label for="name">Email</label><br>
    <input class="form-textbox" type="email" name="email" required><br><br>
    <label for="study">Study and year</label><br>
    <input class="form-textbox" type="text" name="study" required><br><br>
    <label>Position interests</label><br>
    <input class="form-checkbox" type="checkbox" name="mechanical" id="mechanical" value="Mechanical Engineer">
    <label class="form-checkbox-label" for="mechanical">Mechanical Engineer</label><br>
    <input class="form-checkbox" type="checkbox" name="embectrical" id="embectrical" value="Embectrical Engineer (embedded/electrical)">
    <label class="form-checkbox-label" for="embectrical">Embectrical Engineer (embedded/electrical)</label><br>
    <input class="form-checkbox" type="checkbox" name="public-relations" id="public-relations" value="Public Relations">
    <label class="form-checkbox-label" for="public-relations">Public Relations</label><br>
    <input class="form-checkbox" type="checkbox" name="graphical-designer" id="graphical-designer" value="Graphical Designer">
    <label class="form-checkbox-label" for="graphical-designer">Graphical Designer</label><br>
    <input class="form-checkbox" type="checkbox" name="it-manager" id="it-manager" value="IT Manager">
    <label class="form-checkbox-label" for="it-manager">IT Manager</label><br>
    <input class="form-checkbox" type="checkbox" name="other" id="other" value="Other">
    <label class="form-checkbox-label" for="other">Other</label><br><br>
    <label for="motivation">Motivation</label><br>
    <textarea class="form-textbox" name="motivation" required rows="4"></textarea><br><br>
    <input type="hidden" name="_next" value="https://delftmercurians.nl/join/#success">
    <input type="hidden" name="_subject" value="Application form response">
    <input type="hidden" name="_captcha" value="false">
    <input type="text" name="_honey" style="display:none">
    <button class="send-button" type="submit">
      <span class="send-button-text">Send</span>
    </button>
  </form>
</div>

<style>
.post-footer {
  display: none;
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
