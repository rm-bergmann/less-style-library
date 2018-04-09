# LESS Style Library

A library of preset styles and mixins to help with faster CSS development.
This LESS architecture is set up so it's namespaced with groups of re-usable mixins in Declarative format.

LESS is declarative and evaluates stylesheets (it does not run like a script from top to bottom),
therefore keep in mind that this library should be imported before all your application custom styles.
LESS lazy loads variables so it will use the last variable definition in scope.

# Install With NPM:
* $ npm i --save-dev less-style-library
* import the library in your application LESS file

## Tip
Create an imports.less file to import all your less files and import this library last - before all other LESS files.

```CSS
@import '/path-to/node_modules/less-style-library/imports';
```

Mixins are only compiled into a stylesheet when they are used, so bear in mind this library does not add
filesize to your compilied CSS file. Only when you use a mixin, those specific styles are compiled.

## Available Color Variables:
These are different shades to CSS default color variables (Except for black & white).
You can override them in your app LESS file as long as the new LESS variables are declared after the mixin imports.

```CSS
@black
@white
@blue 
@green
@red   
@purple
@orange
@yellow
@pink 
@gray
```

## More shades:
You can suffix the above variables (except for black and white) with '-light' and '-dark'

```CSS
@blue-light 
@green-light
@red-dark
@purple-dark
```

## Primary and Secondary Color Variables
You can override these variables with your choice of colours

```CSS
@col-primary    /* @blue */
@col-secondary  /* @gray-light */
```

## Screen Size Variables for media queries:

Target below 320px:

```CSS
@media @tiny-screen-max {} 
```

Target above 320px:

```CSS
@media @tiny-screen-min {}
```

Target below 479px

```CSS
@media @small-screen-max {}
```

Target above 420px

```CSS
@media @small-screen-min {}
```

More Target Screen Sizes:

```CSS
@media @medium-screen-max {};
@media @medium-screen-min {};
@media @medium-plus-screen-max {};
@media @medium-plus-screen-min {};
@media @large-screen-screen-max {};
@media @large-screen-screen-min {};
@media @x-large-screen-screen-max {};
@media @x-large-screen-screen-min {};
@media @hd-screen-screen-max {};
@media @hd-screen-screen-min {};
```

CSS Grid Style

## Borders

Black solid 1px border (default):

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

If you need paralell top & bottom or left & right borders pass in vertical or horizontal:

```CSS
#border.solid(vertical, 4px, #ccc);
```

## Positioning

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

If the width and height are the same values pass in the type 'equal', then the desired value (default is set to 100px)

```CSS
#display.dimensions(equal, 200px);
```

To style a div as a block use the following mixin:
You can pass in the size (width & height are always equal), background-color, border-radius and padding values:

```CSS
#display.block();
#display.block(200px, red, 8px, 20px);
```

When you float an element's children left or right, apply this mixin so the parent can retain it's height:

```CSS
#display.clearfix();
```

When you target the :before and :after pseudo elements apply this mixin to display it.
This adds the following styles: display: block; content: '';
You can change the content value by passing it in:

```CSS
#display.pseudo();
#display.pseudo(x);
```

If you want to show / hide on specific devices you can use these mixins, as they will take care of the media queries:

```CSS
#display.mobile();
#display.tablet();
#display.desktop();
```

## Button Mixins

Plain flat button style, you can pass in your color of choice (defaults to @col-primary):

```CSS
#button.flat(green)
```

Plain flat button style, slight round edges:
```CSS
#button.flat(round-edge, red);
```

Plain Flat, Round Button Style
```CSS
#button.flat(round, blue);
```

Style a link anchor tag as a button, pass in your color of choice:
```CSS
#button.link(green);
```

## Shapes
For custom shapes there is a mixin for arrow styles.
Pass in the direction (up, down, left or right), size and color

```CSS
#shape.arrow(left, 10px, blue);
```

## More Coming Soon. Stay tuned!
