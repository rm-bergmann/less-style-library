# LESS Style Library

A library of preset styles and mixins to help with faster CSS development.
This LESS architecture is set up so it's namespaced with groups of re-usable mixins in Declarative format.

LESS is declarative and evaluates stylesheets (it does not run like a script from top to bottom),
therefore keep in mind that this library should be imported before all your application custom styles.
LESS lazy loads variables so it will use the last variable definition in scope.

# Install With NPM:

```bash
$ npm i --save-dev less-style-library
```

# Import the library in your application.

I create a new LESS file called imports.less and use a CSS import to import all my LESS files
with a relative import. I have not tried importing it in an index.js file with an absolute import.
I will test that soon.

```CSS
@import '../node_modules/less-style-library/imports';
```
Remember to check the relative path to you're application's node_modules.

Make sure this library is imported *before* all other LESS files in the application.
This will allow you to override the default variables. For example, if you want to set your
own colors:

/* Default */
```css
@blue: #003bff;

/* Override */
@blue: #000e8c;

p {
  color: @blue;
}
```

Compiles to:
```css
p {
  color: #000e8c;
}
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
@teal
@cyan
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
@media @mobile-small-max {
  // Insert styles
} 
```

Target above 320px:

```CSS
@media @mobile-small-min {
  // Insert styles
}
```

Target below 479px

```CSS
@media @mobile-large-max {
  // Insert styles
}
```

Target above 480px

```CSS
@media @mobile-large-min {
  // Insert styles
}
```

More Target Screen Sizes:

```CSS
@media @tablet-small-max {};
@media @tablet-small-min {};
@media @tablet-large-max {};
@media @tablet-large-min {};
@media @desktop-small-max {};
@media @desktop-small-min {};
@media @desktop-large-max {};
@media @desktop-large-min {};
@media @hd-max {};
@media @hd-min {};
```

# CSS Grid Styles
### Apply these mixins to the grid container element

Default: 12 columns, 20px Gap, 1 row auto height
```CSS
.grid-container {
  #display.grid();
}
```

Maybe you want a 4 column grid, 40px gap, 4 rows, 40px row height
```CSS
#display.grid(4, 40px, 4, 40px);
```

Try a 16 column grid, 10px gap, 2 rows, 100px row height
```CSS
#display.grid(16, 10px, 2, 100px); 
```

We can also justify content, justify items and align items all in the center like this:
```CSS
#display.grid(center, 16, 10px, 2, 100px); 
```

You can also try stretch items
```CSS
#display.grid(stretch, 16, 10px, 2, 100px); 
```

### Apply these grid mixins to the grid items inside the grid cotainer:

Default will start at column 1 and end at column 12.
```CSS
.grid-item {
  #grid.column();
}
```

You can customize your start / end points by specifying them.
Lets say we want to start at column 2 and end at column 4:
```CSS
  #grid.column(2, 4);
```

We can also specify the row start / row end like this:
Default will start at row 1 and end at row 2, but we can speficy any row start and end points:
```CSS
  #grid.row();
  #grid.row(3, 5);
```

If you want an element to span across the whole row from left to right use this mixin:
```CSS
  #grid.column(across);
```

If that does not work, you can specify how many columns to span by.
Default starts at column 1 and spans 12 columns.
You can speicfy the start columns and the amount of columns you want to span by. Lets start at column 2 and span 6:
```CSS
  #grid.column(span);
  #grid.column(span, 2, 6);
```

When designing responsive sites we may have columns stacked on top of eachother on mobile devices,
and beside eachother on tablet devices and desktop screens. I have designed some customizeable mixins which
do this work for you.

By default, on tablet and desktop devices we start at column 1 and span 2.
We can specify the start column and amount to span the element by. Lets start at column 6 and span 4:

```CSS
  #grid.column(responsive);
  #grid.column(responsive, 6, 4);
```

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

To align children to left (start) or right (end) of a container apply the following mixin to the container element

```CSS
#display.flex(start);
#display.flex(end);
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
#display.pseudo('&raquo;');
```

If you want to show / hide on specific devices you can use these mixins, as they will take care of the media queries:

```CSS
#display.mobile();
#display.tablet();
#display.desktop();
```

I have a mixin for a situation where Chrome doesn't render webfonts. (This may have been a bug and fixed in a later version).
```CSS
#display.webkit-delay();
```

## Font mixins

Turn 4 lines of code into 1 with the following mixin. It takes font-size, font-weight, line-height and text-align.
The defaults are set as: font-size: 1em; font-weight: 400; line-height: 1; and text-align: left;
To change the defaults, just pass in your custom values. Lets set a center-aligned, 14px bold font with 1.2 line height: 
```CSS
#font.settings(); /* defaults */
#font.settings(14px, bold, 1.2, center);
```

We don't always use all of the styles, so there's another 3 mixins with the above styles broken down:
The first and default font sizing mixin will add font-size, font-weight and line-height, same default values as the font settings mixin.
```CSS
#font.size();
#font.size(20px, 700, 1.3);
```

For only font-size and font-weight, pass in 'font-weight':
```CSS
#font.size(font-weight);
#font.size(font-weight, 1.2rem, bold);
```

For only font-size and line-height, pass in 'line-height':
```CSS
#font.size(line-height);
#font.size(line-height, 18px, 1.2);
```

## Image replacement / Hiding text
I like using the following mixins for image replacement / hiding text:
The first is for default image replacement, and the second one is more accessibilty friendly.
```CSS
#hide.text();
#hide.text(accessible);
```

Use this if you need both ```display: none``` and ```visbility:hidden``` styles.
```CSS
#hide.element();
```

## Form field styles

You can style a form input field with the following mixin:
```CSS
#form.input();
```

## Button Mixins

Plain flat button style, you can pass in your color of choice (defaults to @col-primary):

```CSS
#button.flat(green);
```

Plain flat button style, slight round edges:
```CSS
#button.flat(rounded, red);
```

Plain Flat, Round Button Style
```CSS
#button.flat(round, blue);
```

You can customize the padding and font-size and border-radius as well if you like:
Param order:
background-color, color, padding, font-size, border-radius
```css
#button.custom(red, white, 20px, 14px, 8px);
```

Style a link anchor tag as a button, pass in your color and background color of choice.
You can also add custom padding, font-size and border-radius values (as above)
```CSS
#button.link(blue, white);
#button.link(gray, black, 10px, 12px, 20px);
```

## Gradient
A nice, simple gradient mixin. By default the top color will be the primary color and bottom the secondary color.
We can pass in the colours of choice
```CSS
#gradient.linear();
#gradient.linear(gray, black);
```

## Shapes
For custom shapes there is a mixin for arrow styles.
Pass in the direction (up, down, left or right), size and color

```CSS
#shape.arrow(left, 10px, blue);
```

You can add a round shape with the following mixin:
You can pass in padding, width and height (as the same value) and background-color.

```CSS
#shape.round();
#shape.round(1em, 100px, @black);
```

### Please check for updates regularly and report any issues in github. 
