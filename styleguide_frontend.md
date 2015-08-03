Front-End Code Guidelines
HTML, CSS/SASS, JS

# Content 

* General Guidelines

    * File names & organization

    * General Formatting Rules (indentation, capitalization)

    * Cross-Browser support

    * Third Party Modules

* Markup

    * Head content

        * Doctype & Encoding

        * Other Head Code

    * General Markup Guideline

* CSS

    * Style Rules

    * Formatting Rules

    * Organization

* SASS

    * Formatting rules

    * Organization

* Javascript

* Snippets

# Backgrounds

* * *


When we at Despark write HTML, CSS/SASS and Javascript we have a certain set of rules and guidelines we stick to. They are related to syntax, formatting, file organization and naming. The purpose of this "Code Guideline" is to improve internal and external (freelancers) collaboration, code quality, and to make projects maintenance easier. You can always propose better practices and they will be considered.

# General Guidelines

* * *


## File Names & Organization

Usually every front-end part of project contains of several HTML, CSS and Javascript files. As a general rule every front-end project starts with: **index.php, style.css and script.js**** **and use the following directory structure:

<pre>
  <code>
/static_html
    index.php
/images /* All images. You can create as many sub directories as you decide */
/fonts /* All font files are stored here*/
/scss  /* Contain the main SCSS file (style.scss) and some helpers for IE support if needed */
    style.css /* Main CSS file */
    /vendor /* All third party CSS’s are stored here */
/js /* All JS files we generate */
    script.js /* Main JS file */
    /vendor /* All third party scripts are stored here. jQuery and plug-ins for example */
  </code>
</pre>


! The names **style.css, script.js and directory structure** are mandatory

## General Formatting Rules

### Indentation

No matter you are writing HTML, CSS or Javascript always use **"Tab Size: 4"****.** Do not use “tabs" or mixed type “spaces and tabs" indentation.

### Capitalization 

Use only lowercase. All code has to be lowercase: This applies to HTML element names, attributes, attribute values (unless text/CDATA), CSS selectors, properties, and property values (with the exception of strings).

<pre>
  <code>
<!-- Not recommended -->
```html
<A HREF="#">Click here</A>

<!-- Recommended -->
<a href="#">Click here</a>

/* Not recommended */
.Nav {
  background-color: #A4B2AC;
}

/* Recommended */
.nav {
  background-color: #a4b2ac;
}
```
  </code>
</pre>


## Cross-Browser support

If legacy browser support is required (older than IE 11) we have to provide graceful degradation and fallbacks but not 1:1 design. Using the CSS hack is not encouraged use conditional includes in HTML header instead.

<pre>
  <code>
  ```html
<!--[if lt IE 9]>
  <link rel="stylesheet" href="css/ie8.css">
<![endif]-->
```
  </code>
</pre>


Or

<pre>
  <code>
  ```html
<!--[if lt IE 7 ]> <body class="ie6"> <![endif]-->
<!--[if IE 7 ]><body class="ie7"> <![endif]-->
<!--[if IE 8 ]><body class="ie8"> <![endif]-->
<!--[if IE 9 ]><body class="ie9"> <![endif]-->
<!--[if !IE]><!--> <body> <!--<![endif]-->
```
  </code>
</pre>


Or you can test if functionality exists by using **[Moderniz**r](http://modernizr.com/).

If you work on Mac OS, install **[VirtualBo**x](https://www.virtualbox.org/) and appropriate versions of Windows and IE and test.

**Third Party Modules**

Almost every project requires using third party software. Usually it is jQuery and some plugins (sliders, modal dialogs etc.). If legacy browser support (IE8, IE9 ) are required in the project the latest version of jQuery we use is 1.10. When we need controls like date pickers, autocomplete inputs, drag drop functionality, accordions etc. most commonly we use jQuery UI.

You should put links to all this scripts in document just before last </body> element as well as other JS scripts you write. 

Some third party components contain style file/s. In such cases do not edit their style definitions directly. Leave them as they are and overwrite definitions you need.

# Markup

* * *


As a rule we use by default HTML5. Test your markup against the[ W3C validator](http://validator.w3.org/), to ensure that the markup is well formed. 100% valid code is not a goal, but validation certainly helps to write more maintainable sites as well as debugging code.

## Head Content

### Doctype & Encoding

As it is mentioned above we use HTML5 therefore you have always to use:

<pre>
  <code>
  ```html
<!doctype html>
```
  </code>
</pre>


Always use **UTF-8** **encoding** and set appropriate language HTML attribute of HTML element. Also ensure that your text editor use proper encoding too.

<pre>
  <code>
  ```html
<!doctype html>
<html lang="bg">
    <head>
     <meta charset="UTF-8">
….
```
  </code>
</pre>


### Other Head Code

Put all links to CSS files in **<head>** element and never in **<body>**. 

Links to Javascripts have to be placed in document body before closing **</body>** element. 

Specifying type attributes in these contexts is not necessary as HTML5 implies **text/css** and **text/javascript** as defaults. This can be safely done even for older browsers. 

<pre>
  <code>
  ```html
<!-- Not recommended -->
<link rel="stylesheet" href="css/style.css" type="text/css">
<script type="text/javascript" src="js/vendor/jquery.min.js"></script>

<!-- Recommended -->
<link rel="stylesheet" href="css/style.css">
<script src="js/vendor/jquery.min.js"></script>
```
  </code>
</pre>


**  **

## General Markup Guideline

### Semantics

Use HTML according to its purpose. Use elements for what they have been created for. For example, use **heading** elements for headings, **p** elements for paragraphs, **a** elements for anchors, etc.

Using HTML according to its purpose is important for accessibility, reuse, and code efficiency reasons.

<pre>
  <code>
<!-- Not recommended -->
```html
<div>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Maxime, incidunt aut amet minus saepe molestias provident itaque nisi?<br>
Repellat quasi numquam quod dicta eveniet ab necessitatibus possimus nulla excepturi voluptatem?</div>

<!-- Recommended -->
<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Maxime, incidunt aut amet minus saepe molestias provident itaque nisi?</p>
<p>Repellat quasi numquam quod dicta eveniet ab necessitatibus possimus nulla excepturi voluptatem?</p>

<!-- Not recommended -->
<div class="list">
  <a href="url.html">List item 1</a>
  <a href="url.html">List item 2</a>
  <a href="url.html">List item 3</a>
  <a href="url.html">List item 4</a>
</div>

<!-- Recommended -->
<ul class="list">
  <li><a href="url.html">List 1</a></li>
  <li><a href="url.html">List 2</a></li>
  <li><a href="url.html">List 3</a></li>
  <li><a href="url.html">List 4</a></li>
</ul>
```
  </code>
</pre>


### HTML Quotation Marks

The HTML5 specification defines quotes around attributes as optional. For consistency with attributes that accept whitespace, all attributes should be quoted. Use double **("")**** **rather than single quotation marks **('')** around attribute values. 

### Using Images

Image formats we usually use are JPG, PNG and SVG. JPG’s are prefered for photos and PNG’s for images with transparency or opacity. We encourage using SVG for icons, charts, etc.

Sometimes happens images to be used as buttons or icons. Never leave only image and always add meaningful text. Use CSS styles to hide text (**text-indent: -9999px or other techniques**).

<pre>
<!-- Not recommended -->
``` html
<a href="url.html">
  <img src="img/red-button.png">
</a>

<!-- Recommended -->
<a href="url.html">
    <img src="img/red-button.png">
    <span>Click me</span>
</a>
```
and then something like this:

a span { text-indent: -9999px; }

or the modern version:
``` css
a span {
  text-indent: 100%;
  white-space: nowrap;
  overflow: hidden; 
}
```
  
</pre>


# CSS

* * *


## Style Rules

### Charset

Start every CSS file with **@charset "utf-8";**** **Try to minify the number of CSS files this way you some http request to server. The best is to use only one file.

### Including

Include the CSS file by using **LINK**  not **@import **and do not include it in **<body>**. Never use inline styles, because this makes maintenance process hard and slow.

### ID and Class Selectors

Where possible, avoid expensive CSS selectors. For example, **avoid the * wildcard selector** and **don't qualify ID and class names with type selectors**. Avoid more than 3 levels of nesting selectors. This is important for the performance when DOM elements are thousands or even tens of thousands.

<pre>
  <code>
/* Not recommended */
```css
section.intro { … }
table#addresses { … }

.wrap .column-left ul li { … }

/* Recommended */

.intro { … }
#addresses { … }

.column-left li { … }
```
  </code>
</pre>


### Shorthand Properties

Use shorthand properties where possible. Using shorthand properties is useful for code efficiency and understandability.

<pre>
  <code>
```css
/* Not recommended */
.toolbar {
  border-top-style: none;
  font-family:"Open Sans", sans-serif;
  font-size: 16px;
  line-height: 1.6;
  padding-bottom: 2em;
  padding-left: 1em;
  padding-right: 1em;
  padding-top: 0;
}

/* Recommended */
.toolbar {
  border-top: 0;
  font: 16px/1.6 ", Open Sans", sans-serif;
  padding: 0 1em 2em;
}
```
  </code>
</pre>


### 0 and Units and Leading 0s

Do not use units after 0 values unless they are required. Do not put 0s in front of values or lengths between 0 and 1. 

<pre>
  <code>
```css
/* Recommended */
padding: 0;
margin-top: 0;
opacity: .54;
```
  </code>
</pre>


### Hexadecimal Notation

For color values that permit it, 3 character hexadecimal notation is shorter.

<pre>
  <code>
```css
/* Not recommended */
color: #eecc44;

/* Recommended */
color: #ec4;
```
  </code>
</pre>


ID and Class Name Delimiters

Do not concatenate words and abbreviations in selectors by any characters other than hyphens, in order to improve understanding and scannability.

<pre>
  <code>
```css
/* Not recommended: does not separate the words "demo" and “image" */
.demoimage {}
/* Not recommended: uses underscore instead of hyphen */
.error_status {}

/* Recommended */
.demo-image {}
.error-status {}
```
  </code>
</pre>


Uppercase texts

Always use **text-transform: uppercase;** instead typing caps letters.

## Formatting Rules

Formatting rules

At minimum, format CSS with selectors on one line and each property on its own line. The declarations are indented as described at beginning of the document.

Also, if you specify multiple selectors, it's a good idea to start each on new line. This prevents lines from growing long and improves readability as well as version control workflow.

<pre>
  <code>
  ```css
.nav {
  color: #4a5b6c;
}

.nav li a:hover,
.nav li a.active {
  color: red;
}
```
  </code>
</pre>


Declaration Order

Try to put declarations in alphabetical order in order to achieve consistent code in a way that is easy to remember and maintain. 

### Declaration Stops

End every declaration with a semicolon for consistency and extensibility reasons.

<pre>
  <code>
  ```css
/* Not recommended */
.test {
  display: block;
  height: 100px  /* ← */
}

/* Recommended */
.test {
  display: block;
  height: 100px;  /* ← */
}
```
  </code>
</pre>


### Property Name Stops

Use a space after a property name’s colon. Always use a single space between property and value (but no space between property and colon) for consistency reasons.

<pre>
  <code>
  ```css
/* Not recommended */
h3 {
  font-weight:bold;
}

/* Recommended */
h3 {
  font-weight: bold;
}
```
  </code>
</pre>


### Declaration Block Separation

Use a space between the last selector and the declaration block. Always use a single space between the last selector and the opening brace that begins the declaration block. The opening brace should be on the same line as the last selector in a given rule.

<pre>
  <code>
  ```css
/* Not recommended: missing space */
#video{
  margin-top: 1em;
}

/* Not recommended: unnecessary line break */
#video
{
  margin-top: 1em;
}

/* Recommended */
#video {
  margin-top: 1em;
}
```
  </code>
</pre>


**Organization**

Try to organize stylesheets in specificity order. This ensures that you take full advantage of inheritance and the cascade. A well ordered stylesheet will be organized something like this:

* **Reset** – ground zero. You can use **normalize.css**

* **Elements** – unclassed **h1**, unclassed **ul**, unclassed **a** etc.

* **Components** — generic, underlying design patterns

* **Modules** – modules are constructed from components and their extensions. Try to make them context independable

* **Misc** – error states etc.

This means that as you go down the document each section builds upon and inherits from the previous one(s). There should be less undoing of styles, less specificity problems and all-round better architected stylesheets.

# SASS

* * *


**[SAS**S](http://sass-lang.com/download.html) is our preprocessor of choice. Use it wisely. Use Sass to make your CSS more powerful but try to avoid deep nesting! Nest only when it would actually be necessary. 

**Formatting rules**

Framework & Grid Systems 

There are a lot of frameworks and plugins for SASS. 

We encourage you to use **[Bourbo**n](http://bourbon.io). It’s definitely one of the better Sass mixin libraries. It is lightweight and simple. As Grid System you can use **[Bourbon Nea**t](http://neat.bourbon.io/) which is a grid system built with Sass and Bourbon. It’s super simple and fully responsive. 

Use Your Regular CSS Formatting Rules / Style Guide

You should follow CSS formatting guidelines you are already read above. In short:

1. Be consistent with indentation. Always use **"Tab Size: 4"**

2. Be consistent about where spaces before/after colons/braces go. Use a space after a property name’s colon. Always use a single space between property and value (but no space between property and colon) for consistency reasons.

3. One selector per line, One rule per line

4. List related properties together

5. Have a plan for class name naming

6. Avoid using ID's

### List @extend(s) First

Knowing first that this class inherits another whole set of rules from elsewhere is good.

<pre>
  <code>
  ```css
.btn {
@extend .btn-small;
// ...
}
```
  </code>
</pre>


List "Regular" Styles Next

<pre>
  <code>
  ```css
.btn {
@extend .btn-small;
width: 80px;
// ...
}
```
  </code>
</pre>


### List @include(s) Next

This visually separates the @extends and @includes as well as groups the @includes for easier reading. You might also want to make the call on separating user-authored @includes and vendor-provided @includes.

<pre>
  <code>
```css
.btn {
@extend .btn-small;
width: 80px;
@include transition(all 0.3s ease-out);
// ...
}
```
  </code>
</pre>


Nested Selectors Last

And nothing goes after the nested stuff. And the same order as above within the nested selector would apply.

<pre>
  <code>
```scss
.btn {
    @extend .btn-small;
    width: 80px;
    @include transition(all 0.3s ease-out);
    span {
        background-color: red;
    }
    img {
        border: 0;
    }
}
```
  </code>
</pre>


### All Vendor Prefixes Use @mixins

Vendor prefixes are a time-sensitive thing so use @mixins. Boubon’s mixin **@prefixer** for example.

<pre>
  <code>
```scss
// SCSS
.box {
    @prefixer(box-sizing, border-box, webkit moz spec);
}

// Produced CSS
.box {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
}
```
  </code>
</pre>


Maximum Nesting: Three Levels Deep

If you're deeper than that, you're writing a crappy selector that it's too reliant on HTML structure (fragile), too specific (too powerful), and not very reusable.

<pre>
  <code>
```scss
.weather {
    .cities {
        li {
              // no more!
        }
    }
}
```
  </code>
</pre>


**Organization**

List Global Dependencies First, Then Author Dependencies, Then Elements, Then Modules

The dependencies like Bourbon, colors, settings and mixins generate no compiled CSS at all, they are purely code dependencies. Listing the Base next means that more specific "parts", which come after, have the power to override patterns without problems.

<pre>
  <code>
```css
/* Vendor/Global Dependencies */
@import "bourbon";
@import "neat";

/* Author Dependencies */
@import "global/settings";
@import "global/helpers";

/* Base */
@import “global/layout";
@import “global/typo";

/* Elements */
@import "elements/tabs";
@import "elements/buttons";

/* Modules */
@import "modules/header";
@import "modules/footer";
```
  </code>
</pre>


### Break Into As Many Small Files As Makes Sense

There is no penalty to splitting into many small files. Do it as much as feels good to the project. Sometimes  it is easier to jump to small specific files and navigate through them than fewer/larger ones. Use partials and name them _partial-name.scss. This is a common naming convention that indicates this file isn't meant to be compiled by itself.

Typically we suggest to separate SCSS’s into following file structure:

<pre>
  <code>
  ```css
style.scss /* Main file no styles directly in them. It is just "table of content" */
    _layout.scss /* Base-level layout (margin, padding, sizing) */
    _base.scss  /* Base-level tags */

/global
    _settings.scss /* Constants and variables - colors, sizes, paddings etc. */
    _helpers.scss  /* Mixins and function definitions */
    _reset.scss     /* Usually this is Normalize.css */
    _animations.scss /* Keyframe animations */
    _typo.scss /* Base-level typography (colors, fonts) */

/elements
    _buttons.scss /* Button’s definitions */
    _form-elements.scss /* Input boxes etc */
    _panels.scss

/modules
    _header.scss
    _footer.scss
    _forms.scss /* Forms’ styling */
    _navigation.scss /* All about site navigation */
    _modals.scss /* Modal dialogs */

/vendor  /* All third party stuff */
```
  </code>
</pre>


# Javascript

* * *


**Modules often in use:**

[Despark wiki page with tools and libraries ](http://dev.despark.com/wiki/index.php/Front-end_Tools_and_Libraries)

All in one UI

**[jQuery U**I](http://jqueryui.com/) - set of user interface interactions, effects, widgets, and themes built on top of the jQuery JavaScript Library.

Animations

**[GSA**P](http://www.greensock.com/gsap-js/) - Professional-Grade HTML5 Animation

Modal Dialogs 

**[jQuery UI Dialo**g](http://jqueryui.com/dialog/)

 

**[Twitter Bootstrap Modal**s](http://getbootstrap.com/javascript/#modals)

**[http://tympanus.net/Development/ModalWindowEffects**/](http://tympanus.net/Development/ModalWindowEffects/)

Charts

**[amChart**s](http://www.amcharts.com/)** - **very powerful but it is not free 

**[Google Chart**s](https://developers.google.com/chart/)

Feature detection

**[Moderniz**r](http://modernizr.com/)

Carousels & Sliders 

[Owl Carousel](http://owlgraphic.com/owlcarousel/) - responsive, touch, nice documentation

**[jCoverfli**p](http://www.jcoverflip.com/) 

**[FlexSlider **2](http://flexslider.woothemes.com/) - responsive, supports touch events

**[Superslide**s](http://nicinabox.com/superslides/) - Full screen slider, supports touch events

[http://tympanus.net/Development/SidebarTransitions/](http://tympanus.net/Development/SidebarTransitions/)

Image galleries

[Lightbox 2](http://lokeshdhakar.com/projects/lightbox2/)

[PrettyPhoto](http://www.no-margin-for-errors.com/projects/prettyphoto-jquery-lightbox-clone/)

# Snippets

* * *


