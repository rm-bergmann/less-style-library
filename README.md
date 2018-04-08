# LESS Style Library

A library of preset styles and mixins to help with faster CSS development.

# Installation:
* $ NPM Install less-style-library
* import the library in your application LESS file

```
@import 'node_modules/less-mixin-library/mixin-imports;'
```

I set up LESS so it's namespaced with groups of re-usable mixins.
I am essentially replacing common groups of styles with 1 line of code, in English readable format (Declarative).

Color Variables:

@black
@white

Screen Size Variables for media queries:

Target below 320px:
```
@media @tiny-screen-max {} 
```

Target above 320px:
```
@tiny-screen-min
```

Target below 479px
```
@media @small-screen-max {}
```

Target above 420px
```
@media @small-screen-min {}
```

More Target Screen Sizes:

```
@media @medium-screen-max {};
@media @medium-screen-min {};
@media @medium-plus-screen-max {};
@media @medium-plus-screen-min {};
@media @large-screen-screen-max {};
@media @large-screen-screen-min {};
@media @x-large-screen-screen-max {};
@media @x-large-screen-screen-min {};
@media @hd-screen-screen-max {};
@media  @hd-screen-screen-min {};
```

CSS Grid Style

## Borders

Black solid border, default:

```CSS
#border.solid();
```

Maybe you want 4px red solid border? No problem, just pass in 4px, and the desired color.

```CSS
#border.solid(4px, #f00);
```

Maybe you want 2px green top border only? Pass in top (or bottom, left, right,) border-width value and color

```CSS
#border.solid(top, 2px, green);
```

## Absolute Positioning

No default included, specify top-left, bottom-left, top-right or bottom-right.
Values default to 0 and 0.
The code below compiles to: position: absolute; top: 0; left: 0;

```CSS
#position.absolute(top-left);
```

Try Positioning absolute, bottom: 10px, right: 5px:

```CSS
#position.absolute(bottom-right, 10px, 5px);
```

You can also position fixed or relative with the same params:

```CSS
#position.relative(top-right, 0, 50%);
#position.fixed(top-left);
```

## Display Mixins

Apply this mixin to the parent element which will align children from left to right with equal spacing.
```CSS
#display.flex(space);
```

To minimize common repeatition, this mixin takes color as the first param and background-color as the second param.
By default color is set to black and background color set to white. Pass in the colours of your choice.

```CSS
/* Default foreground and background colors: color: black; background-color: white */
#display.colours();

/* color: white; background-color: blue */
#display.colours(white, blue);
```

Width and height are common styles to add to elements, use this mixin if width and height are different values:
The first param is the width value, the second param is the hight value:
```CSS
#display.dimensions(200px, 50px);
```

If the width and height are the same values pass in the type "equal", then the desired value (default is set to 100px)
```CSS
#display.dimensions(equal, 200px);
```

When you float an elements children left or right, apply this mixin so the parent can retain it's height:
```CSS
#display.clearfix();
```

When you target the :before and :after pseudo elements apply this mixin to display it.
```CSS
#display.pseudo();
```

If you want to show / hide on specific devices you can use these mixins, as they will take care of the media queries:
```CSS
#display.mobile();
#display.tablet();
#display.desktop();
```

## Button Mixins

Style a link as buttons.
```CSS
#button.link();
```

## More Coming Soon. Stay tuned!
