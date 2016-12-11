###Responsive Design Notes

Viewport
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
Media Queries
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

Flex-box

On the parent flex container.  Flex-wrap tells browser its OK for elements to wrap to the next line
```CSS
.container{
  width: 100%;
  display: flex;
  flex-wrap: wrap;

}
```
Change the order of elements with the order attribute on media queries
* Example:
```CSS
@media screen and (min-width: 700px){
  .dark_blue { order: 4; }
  .light_blue { order: 5 }
  .green { order: 2 }
  .orange { order: 3 }
  .red { order: 1 }
}
```
