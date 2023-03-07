---
ShowToc: false
ShowBreadcrumbs: false
hideMeta: true
ShowRssButtonInSectionTermList: false
layout: "single"
---

<img src="/images/logo.svg" class="logo-home" alt="Delft Mercurians Logo" />
<p class="summary-home">We are a RoboCup team based in Delft, created in 2022</p>
<div class="buttons">
  <a class="button" href="about/" rel="noopener" title="About">
    <span class="button-inner">
      About
    </span>
  </a>
  <a class="button" href="contact/" rel="noopener" title="Contact">
    <span class="button-inner">
      Contact
    </span>
  </a>
</div>


<div class="pagespacer-home"></div>
<div class="sponsorcontainer-home">
    <a href="https://rsadelft.nl" class="sponsorlink-home">
      <img src="/images/rsa_logo.svg" alt="Robotics Student Association" class="sponsor-home" />
    </a>
    <a href="https://en.nanotec.com" class="sponsorlink-home">
      <img src="/images/nanotec_logo.svg" alt="Nanotec" class="sponsor-home" />
    </a>
    <a href="https://robohouse.nl" class="sponsorlink-home">
      <img src="/images/robohouse_logo.png" alt="Robohouse" class="sponsor-home" />
    </a>
</div>

<style>
.logo-home {
  display: block; 
  margin-left: auto !important; 
  margin-right: auto !important;
  width: 500px;
}
body.dark .logo-home {
  content: url("/images/logo_dark.svg");
}
.title-home {
  text-align: center;
  font-size: 28px !important;
}
.summary-home {
  text-align: center;
}

.button {
  box-shadow: none !important;
}

.sponsorcontainer-home {
  margin-top: 50px;
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
.sponsor-home {
  height: 50px;
}
.sponsorlink-home {
  color: transparent;
}
.pagespacer-home {
  height: calc(100vh - 1000px);
}
 
.post-footer {
  display: none;
}
  
body {
  background-image: url("/images/football_background.svg") !important;
}
body.dark {
  background-image: url("/images/football_background_dark.svg") !important;
}
</style>
