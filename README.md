<style>@import url('https://fonts.googleapis.com/css?family=Lato:400,700,900');

// ===Color
$c-base: #333;
$c-base-dark: #111;
$c-primary: #6fd1bd;
$c-secondary: salmon;
$c-keyline: #ddd;
$c-bg: #fff;
$c-link: $c-base;
$c-heading: $c-base-dark;

// ===Base
// Type
$enable-fontSmoothing: true;
$b-fontSize: 1.6rem;
$b-fontFamily: Lato, Helvetica, Arial, sans-serif;
$b-fontWeight: normal;
$b-letterSpacing: 0.008em;
$b-lineHeight: 1.5;
// Animation
$b-animType: ease-in-out; 
$b-animSpeed: 0.2s;
$b-shadowSize: 4px;

// ===Navbar
$Navbar-color: #fff;
$Navbar-bg: #111;
$Navbar-itemLineHeight: 4rem;

// ===Footer
$Footer-gap: unitSize(2);

// ===================================
// Basic
//

@at-root {

  html {
    font-size: 62.5%;
    box-sizing: border-box;
  }

  *, *:before, *:after {
    box-sizing: inherit;
  }

  body {
    margin: 0;
    background-color: $c-bg;
  }

  img {
    max-width: 100%;
    height: auto;
  }

}


// ==============================
// Utilities
//

@at-root {

  .u-cf {
    &:before,
    &:after {
      content: " ";
      display: table;
    }
    &:after {
      clear: both;
    }
  }

  .u-hug {
    margin-top: 0 !important;
  }

  .u-pullRight {
    float: right;
  }

  .u-keyline {
    position: relative;
    &:before {
      content: "";
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      border-top: 1px solid $c-keyline;
    }
  }
  
  .u-link {
    display: inline;
    position: relative;
    background-image: linear-gradient(to bottom,lighten($c-primary, 10) 0,lighten($c-primary, 10) 100%);
    background-position: 0 100%;
    background-repeat: repeat-x;
    background-size: 2px 2px;
    border-bottom: 0;
    text-decoration: none;
    &:hover {
      background-image: linear-gradient(to bottom,lighten($c-secondary, 10) 0,lighten($c-secondary, 10) 100%);
    }
  }

  .u-shadow {
    text-shadow: $b-shadowSize $b-shadowSize 0 $c-primary;
    transition: text-shadow $b-animSpeed $b-animType;
    @at-root a:hover #{&} {
      text-shadow: (-$b-shadowSize) (-$b-shadowSize) 0 $c-secondary;
    }
  }

  @include media-breakpoint-down(sm) {
    .u-hidden\@sm-down {
      display: none !important;
    }
  }

  @include media-breakpoint-down(xs) {
    .u-hidden\@xs-down {
      display: none !important;
    }
  }

}


// ==============================
// Typography
// 

@at-root {

  body {
    color: $c-base;
    font-size: $b-fontSize;
    font-family: $b-fontFamily;
    font-weight: $b-fontWeight;
    line-height: $b-lineHeight;
    @if ($b-letterSpacing) {
      letter-spacing: $b-letterSpacing;
    }
    @if ($enable-fontSmoothing) {
      -webkit-font-smoothing: antialiased;
      -moz-osx-font-smoothing: grayscale;
    }
  }

  h1, h2, h3, h4, h5, h6 {
    color: $c-heading;
    line-height: 1.2;
    font-weight: 900;
  }

  h1, h2, h3, h4, h5, h6, ul, p {
    margin-top: unitSize(2);
    margin-bottom: 0;
  }

  h3, .h3 {
    font-size: 2rem;
    margin-top: unitSize(4);
  }

  a {
    color: $c-link;
  }

  ul {
    padding-left: 1.8rem;
  }

  .Title {
    @include responsive-font(8vw, 42px, 75px, 50px);
    font-family: Lato, 'Open Sans', Helvetica, Arial;
    font-weight: 900;
    line-height: 1.1;
    margin-top: 0;
    margin-bottom: 0;
    text-transform: uppercase;
    display: inline-block;
    &-sub {
      font-size: 0.34em;
      letter-spacing: 0.16em;
      font-weight: 400;
      text-transform: none;
      display: block;
      margin-top: unitSize(1.5);
      padding-top: unitSize(2);
      border-top: 0.45em solid;
    }
  }

}


// ==============================
// Layout 
// 

@at-root {

  .l-Wrapper {
    width: 80%;
    max-width: 90rem;
    margin-left: auto;
    margin-right: auto;
  }
  
   @include media-breakpoint-down(sm) {
    .l-Wrapper--reset\@sm-down {
      width: 100%;
    }
  }


  // 
  // Header
  // 

  .l-Header {
    margin-top: unitSize(8);
    margin-bottom: unitSize(4);
    &-col {
      margin-top: unitSize(4);
      margin-bottom: unitSize(4);
    }
    @include media-breakpoint-up(sm) {
      display: flex;
      justify-content: space-between;
      align-items: flex-end;
      &-col {
        &:last-child:not(:first-child) {
          text-align: right;
        }
      }
    }
  }


  // 
  // Sections
  // 

  @at-root {

    .l-Section {
      margin-top: unitSize(8);
      + .l-Section {
        position: relative;
        border-top: 1px solid $c-keyline;
        &:before {
          content: "";
          @include responsive-font(8vw, 42px, 75px, 50px);
          position: absolute;
          top: unitSize(0, -0.1);
          border-top: (0.34em * 0.45) solid;
          width: unitSize(5);
        }
      }
    }

    .l-Section-title,
    .l-Section-content {
      margin-top: unitSize(4);
    }

    .l-Section-content {
      > :first-child {
        margin-top: 0;
      }
      > p:first-child,
      > ul:first-child {
        margin-top: 0.3rem;
      }
    }

    @include media-breakpoint-up(md) {
      .l-Section {
        display: flex;
        &:before {
          display: none;
        }
      }
      .l-Section-title {
        flex: 0 0 24%;
      }
    }

  }


  // 
  // Footer
  // 

  .l-Footer {
    font-size: 1.4rem;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    margin: unitSize(16) ($Footer-gap / -2) unitSize(4);
    padding-top: unitSize(4);
    a {
      text-decoration: none;
      display: inline-block;
      &:not(:last-child) {
        margin-right: $Footer-gap;
      }
      &:hover {
        color: $c-base-dark;
      }
    }
    &-col {
      padding-left: $Footer-gap / 2;
      padding-right: $Footer-gap / 2;
    }
  }

}


// ==============================
// Navbar
// 

@at-root {

  .Navbar {
    color: $Navbar-color;
    font-size: 1rem;
    font-weight: bold;
    line-height: $Navbar-itemLineHeight;
    letter-spacing: 0.28rem;
    text-transform: uppercase;
    width: 100%;
    background-color: $Navbar-bg;
    a:not(.Navbar-toggle) {
      color: inherit;
      text-decoration: none;
    }
    ul {
      @extend %resetList;
    }
    li {
      display: inline-block;
    }
    a {
      display: block;
      padding: 0 unitSize(1);
    }
  }

  a.Navbar-btn {
    padding-left: unitSize(2.5);
    padding-right: unitSize(2.5);
    background: $c-primary;
    &:hover {
      background: $c-secondary;
    }
  }
  
  @include media-breakpoint-down(sm) {
    .Navbar {
      text-align: right;
      ul:not(:first-child) {
        display: inline-block;
        padding-right: unitSize(2) !important;
      }
    }
  }

}


// ==============================
// Tags
// 

.Tag {
  color: $c-base-dark;
  text-shadow: 1px 1px 0 rgba(white, 0.4);
  font-weight: 700;
  line-height: 1;
  position: relative;
  display: inline-block;
  padding-left: unitSize(1);
  padding-right: unitSize(1);
  &:before {
    content: "";
    position: absolute;
    z-index: -1;
    top: 0;
    left: 0;
    right: 0;
    height: 1em;
    bottom: 0;
    margin: auto;
    border-radius: 0.2rem;
    background-color: rgba($c-primary, 0.5);
    transition: all 0.8s 0.4s $b-animType;
  }
  &:hover {
    &:before {
      transform: scale(1.05, 2.4);
      background-color: rgba($c-primary, 1);
      transition-delay: 0s;
      transition-duration: $b-animSpeed;
    }
  }
}


// ==============================
// Print
//

@media print {
  
  html {
    font-size: 50%;
  }
  
  .l-Wrapper {
    width: 100%;
    max-width: none;
  }

  .Navbar,
  .u-hidden\@print {
    display: none;
  }
  
  .l-Header,
  .l-Header-col {
    margin-top: 0;
  }
  
  .l-Footer,
  .l-Section {
    margin-top: unitSize(4);
  }
  
  h3, .h3, 
  .l-Section-title, 
  .l-Section-content {
    margin-top: unitSize(2);
  }

  .Title {
    font-size: 4.5rem;
  }

  .l-Header {
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
    &-col {
      &:last-child:not(:first-child) {
        text-align: right;
      }
    }
  }

  .l-Section {
    position: relative;
    padding-top: 5px;
    border-top: 1px solid $c-keyline;
    &:before {
      display: none;
    }
    &:after {
      content: "";
      position: absolute;
      top: -1px;
      left: 0;
      border-top: 5px solid;
      width: unitSize(5);
    }
  }

  .Tag {
    font-weight: 900;
    display: inline;
    padding-left: 0;
    padding-right: 0;
  }

  *,
  *:before,
  *:after,
  p:first-letter,
  div:first-letter,
  blockquote:first-letter,
  li:first-letter,
  p:first-line,
  div:first-line,
  blockquote:first-line,
  li:first-line {
    background: transparent !important;
    color: #000 !important;
    box-shadow: none !important;
    text-shadow: none !important;
  }

  a,
  a:visited {
    text-decoration: underline;
  }

  p,
  h2,
  h3,
  li {
    orphans: 3;
    widows: 3;
  }

  h2,
  h3 {
    page-break-after: avoid;
    color: red;
  }

}

@page { margin: 2.2cm 2.2cm 1.8cm; }
</style>
<nav class="Navbar">
  <div class="l-Wrapper l-Wrapper--reset@sm-down">
    <ul class="u-pullRight u-hidden@xs-down">
      <li>
        <a class="Navbar-btn Navbar-btn--main" href="http://sonjastrieder.com/download/sonja-strieder-frontend-ui-developer.pdf" target="_blank">Download 
          <span>(pdf)</span>
        </a>
      </li>
    </ul>
    <ul>
      <li><a href="https://www.linkedin.com/in/sonjastrieder" target="_blank">Linkedin</a></li>
      <li><a href="https://twitter.com/sonjastrieder" target="_blank">Twitter</a></li>
      <li><a href="https://codepen.io/sonjastrieder" target="_blank">Codepen</a></li>
    </ul>
  </div>
</nav>

<article class="l-Wrapper">

  <div class="l-Header">
    <div class="l-Header-col">
      <a href="http://www.sonjastrieder.com" target="_blank">
        <h1 class="Title">
          <span class="u-shadow">
            Sonja<br>
            Strieder
          </span>
          <span class="Title-sub">Front-end UI developer</span>
        </h1>
      </a>
    </div>
    <div class="l-Header-col Contact">
      <div>Seattle, WA</div>
      <div><a class="u-link" href="http://sonjastrieder.com/" target="_blank">www.sonjastrieder.com</a></div>
      <div><a class="u-link" href="mailto:sonja.strieder@gmail.com" target="_blank">sonja.strieder@gmail.com</a></div>
    </div>
  </div>

  <section class="l-Section">
    <h2 class="l-Section-title h3 u-hidden@sm-down">Profile</h2>
    <div class="l-Section-content">
      <p>I specialize in component based HTML/CSS architecture, with a focus on maintainability and scalability, a mobile first approach.</p>
    </div>
  </section>

  <section class="l-Section">
    <h2 class="l-Section-title h3">Skills</h2>
    <div class="l-Section-content">
      <ul>
        <li>Highly skilled in creating performant <strong class="Tag">HTML</strong>, <strong class="Tag">CSS</strong></li>
        <li>Passionate about <strong class="Tag">CSS Methodologies</strong> and <strong class="Tag">CSS Preprocessors</strong></li>
        <li>Skilled in creating <strong class="Tag">Component Libraries</strong>, <strong class="Tag">Prototypes</strong> and <strong class="Tag">Style Guides</strong></li>
        <li>Experienced with <strong class="Tag">Templating Languages</strong> and <strong class="Tag">JavaScript</strong></li>
        <li>Proficient with <strong class="Tag">Task Runners</strong> and <strong class="Tag">Package Managers</strong> and <strong class="Tag">Version Control Systems</strong></li>
        <li>Knowledgeable about <strong class="Tag">User Experience</strong>, <strong class="Tag">Accessibility</strong>, <strong class="Tag">Performance</strong>, <strong class="Tag">Responsive Web Development</strong> with a <strong class="Tag">Mobile First</strong>          approach, <strong class="Tag">Cross-Browser Compatibilities</strong> and <strong class="Tag">Progressive Enhancement</strong>.</li>
      </ul>
    </div>
  </section>

  <section class="l-Section">
    <h2 class="l-Section-title h3">Experience</h2>
    <div class="l-Section-content">
      <h3>Freelance Front-end Developer</h3>
      <a class="u-link" href="http://www.sonjastrieder.com/" target="_blank">Self-employed, Seattle</a> (WA)<br> May 2017 - present

      <h3>Front-end Developer</h3>
      <a class="u-link" href="https://www.snaptechnology.co.uk/" target="_blank">Snap Fashion, London</a> (UK)<br> May 2014 - Jul 2016
      <ul>
        <li>Re-architected CSS/HTML codebase of the responsive Snap Fashion website for better maintainability and performance.</li>
        <li>Introduced Grunt, Bower and npm to automate common tasks, optimize frontend assets and manage third party packages.</li>
        <li>Created and maintained a style guide to use as a reference for our design language.</li>
        <li>Delivered front-end work for various external and internal projects to the backend team.</li>
        <li>Built a JavaScript widget for integration of product feeds on third party websites using the Snap Fashion API.</li>
        <li>Developed prototypes including a Chrome extension and browser bookmarklet.</li>
        <li>Offered guidance and support to the design team, advising on core web design principles, best practice and work flow.
        </li>
      </ul>

      <h3>Web Design & Interface Specialist</h3>
      <a class="u-link" href="http://www.johnhenry.net/" target="_blank">JohnHenry, London</a> (UK)<br> Jun 2010 - May 2014
      <ul>
        <li>Working within a team of 16+ I’ve established myself as a front-end developer with a strong focus on web standards, semantics, accessibility and progressive enhancement (HTML/CSS).</li>
        <li>Designed and/or built Wordpress themes as well as Shopify themes from scratch or customized them depending on the client’s needs.</li>
        <li>Headed the design team and designed simple and clean user interfaces.
        </li>
      </ul>

      <h3>Web Specialist</h3>
      <a class="u-link" href="http://www.johnhenry.net/" target="_blank">JohnHenry, London</a> (UK)<br> Oct 2009 - Jun 2010
      <ul>
        <li>Designed client websites and features as well as customized social media channels to improve their online presence.</li>
        <li>Content management, including image processing for the web.</li>
        <li>Built HTML newsletters and managed the distribution through the in house newsletter management system.</li>
        <li>Assisted the development team with HTML and CSS updates
        </li>
      </ul>
    </div>
  </section>

  <section class="l-Section">
    <h2 class="l-Section-title h3">Education</h2>
    <div class="l-Section-content">
      <h3>BSc, Media-technology and -design</h3>
      <a class="u-link" href="https://www.fh-ooe.at/en/hagenberg-campus/" target="_blank">University of Applied Sciences Campus Hagenberg</a> (AUT)<br> 2006 - 2009
      <p>A full-time degree programme that provides the technical expertise as well as the design and communication skills in areas including web (backend and frontend development), multimedia, 3D modelling, animation, audio & video production.</p>
    </div>
  </section>

  <section class="l-Section u-hidden@print">
    <h2 class="l-Section-title h3">Interests</h2>
    <div class="l-Section-content">
      <p>User Experience, Accessibility, Web Standards, Automatization, Technology, Simplicity, Snowboarding, Bouldering, Coffee, Food, Art, Music, Movies, Traveling, Cabins, Plants, Goats, Chickens</p>
    </div>
  </section>
</article>

<div class="l-Wrapper u-keyline">
  <div class="l-Footer">
    <div class="l-Footer-col">
      <strong class="Tag">S. Strieder</strong>
    </div>
    <div class="l-Footer-col Contact">
      <a href="http://sonjastrieder.com" target="_blank">sonjastrieder.com</a>
      <a href="mailto:sonja.strieder@gmail.com" target="_blank">sonja.strieder@gmail.com</a>
    </div>
  </div>
</div>
