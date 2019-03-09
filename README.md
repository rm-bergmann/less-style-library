# LESS Style Library

A library of preset styles, variables and mixins to help with faster CSS development.
The LESS architecture is set up so it's namespaced with groups of re-usable mixins in Declarative format.

LESS is declarative and evaluates stylesheets (it does not run like a script from top to bottom),
therefore keep in mind that this library should be imported before all your application custom styles.
LESS lazy loads variables so it will use the last variable definition in scope.

# Install With NPM, -D Flag = --save-dev:

```bash
$ npm i -D less-style-library
```

# Import the library in your application.

I create a new LESS file called imports.less and use a CSS import to import all my LESS files
with a relative import. I have not tried importing it in an index.js file with an absolute import.
I will test that soon.

```CSS
@import '{path_to}/node_modules/less-style-library/imports';
```

Import the library *before* all other LESS files in the application.
This will allow you to override the default variables with your custom values.

Mixins are only compiled into a stylesheet when they are used, so bear in mind this library does not add
filesize to your compilied CSS file. Only when you use a mixin, those specific styles are compiled.

By default, all default color parameters are set to @color-01 which is set to @blue. You can override @color-01
with a different color variable or a color of choice. You can change all color variables with your hex color of choice.

For all the documentation, guides and examples on how to use this library please visit the [documentation website](http://less.rickbergmann.com)


### Please check for updates regularly and report any issues in github. Contributions welcome.
