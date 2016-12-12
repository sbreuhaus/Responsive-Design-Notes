##Responsive Design Notes

##Harware pixels VS Device Independent pixels (Dips)
The browser reports the number of pixels as dips, not hardware.  Dips is a unit of measurement that relates pixels to a real distance.  The idea is that a Dip will take up the same amount of space on any display regardless of the pixel density of the display.  For example, a device width of 2560 device pixels will have a width of 1280 Dips if there is a device pixel ratio of two.  

##Viewport
Unless you tell the browser your site was designed to work on a small screen, it assumes that it wasn't.
It renders the page as if it were on a screen that is 980 Dips wide.  The browser also scales the content, rather than letting it re-flow.  If the screen is a phone that is only 360 dips, the content will be scaled to less than half and look terrible.  Insert this meta tag to avoid that.
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
##Four Most Common Layout Patterns
* Mostly Fluid
* Column Drop
* Layout Shifter
* Off Canvas

##Off Canvas
* Often used as hidden navigation on small screens until the "hamburger" is clicked.  
```html
<nav id="drawer" class="dark_blue"></nav>

<main class="light_blue"></main>
```
```CSS
html, body, main {
  height: 100%;
  width: 100%;
}
```
* Set style for off-canvas Nav element
```CSS
nav {
  width: 300px;
  position: absolute;
  /* This trasform moves the drawer off canvas. */
  -webkit-transform: translate(-300px, 0);
  transform: translate(-300px, 0);
  /* Optionally, we animate the drawer. */
  transition: transform 0.3s ease;
}
nav.open {
  -webkit-transform: translate(0, 0);
  transform: translate(0, 0);
}
```
* Once the screen grows to a certain size(600px) a media query sets the two divs back to their normal spot.
```CSS
@media screen and (min-width: 600px){
  nav {
    position:relative;
    transform:translate(0,0);
  }
  body {
    display: flex;
    flex-flow: nowrap;
  }
  main {
    width: auto;
    flex-grow: 1;
  }
}
```
* A javascript event listener is needed to toggle the nav.
```js
menu.addEventListener('click', function(e) {
  drawer.classList.toggle('open');
  e.stopPropagation();
});
```

##Media Queries
* Use content as a guide for breakpoints, not a device
* Start design for phone and then work up to tablet and finally desktop
* Can reference a specific style sheet for a specific screen size.  However this results in additional http  requests which can slow the site down

```html
<link rel="stylesheet" media="screen and (min-width: 550px)" href="name-of-stylesheet.css">

```
* Or use @media in CSS.  Results in less stylesheets
```CSS
@media screen and (min-width: 0px) and (max-width: 400px) {
  body {background-color: red;}
}

@media screen and (min-width: 401px) and (max-width: 599px) {
  body {background-color: green;}
}

@media screen and (min-width: 600px) {
  body {background-color: blue;}
}
```

###Flex-box

On the parent flex container.  Flex-wrap tells browser its OK for elements to wrap to the next line
```CSS
.container{
  width: 100%;
  display: flex;
  flex-wrap: wrap;

}
```
Change the order of elements with the order attribute on media queries
```CSS
@media screen and (min-width: 700px){
  .dark_blue { order: 4; }
  .light_blue { order: 5 }
  .green { order: 2 }
  .orange { order: 3 }
  .red { order: 1 }
}
```
Add a margin to Flex container once it passes the largest width desired
```CSS
@media screen and (min-width: 800px) {
  .container {
    width: 800px;
    margin-left: auto;
    margin-right: auto;}
}
```
