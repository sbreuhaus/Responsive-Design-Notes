Responsive-Design-Notes

Viewport
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
Media Queries
* Use content as a guide for breakpoints, not a device
* Start design for phone and then work up to tablet and finally desktop
* Can reference a specific style sheet for a specific screen size

```html
<link rel="stylesheet" media="screen and (min-width: 550px)" href="name-of-stylesheet.css">

```
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
