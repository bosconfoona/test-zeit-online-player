# ZEIT Player test from npm-build-boilerplate 

## Install and DEV

After cloning go to Terminal and in the repo folder run:

npm i (installs all dependencies and starts a server on localhost:3000)

or for further developement 

npm watch (starts the server and watches files for changes)

## IF Errors
Install an older version of node-sass (npm install node-sass@4.12.0 --save)

Working with:
node -v
v14.2.0

npm -v
6.14.4

## List of available tasks
### `clean`
  `rm -f dist/{css/*,js/*,images/*}`

  Delete existing dist files

### `autoprefixer`
  `postcss -u autoprefixer -r dist/css/*`

  Add vendor prefixes to your CSS automatically

### `scss`
  `node-sass --output-style compressed -o dist/css src/scss`

  Compile Scss to CSS

### `lint`
  `eslint src/js`

  "Lint" your JavaScript to enforce a uniform style and find errors

### `uglify`
  `mkdir -p dist/js && uglifyjs src/js/*.js -m -o dist/js/app.js && uglifyjs src/js/*.js -m -c -o dist/js/app.min.js`

  Uglify (minify) a production ready bundle of JavaScript

### `imagemin`
  `imagemin src/images/* -o dist/images`

  Compress all types of images

### `icons`
  `svgo -f src/images/icons && mkdir -p dist/images && svg-sprite-generate -d src/images/icons -o dist/images/icons.svg`

  Compress separate SVG files and combine them into one SVG "sprite"

### `serve`
  `browser-sync start --server --files 'dist/css/*.css, dist/js/*.js, **/*.html, !node_modules/**/*.html'`

  Start a new server and watch for CSS & JS file changes in the `dist` folder

### `build:css`
  `run-s scss autoprefixer`

  Alias to run the `scss` and `autoprefixer` tasks. Compiles Scss to CSS & add vendor prefixes

### `build:js`
  `run-s lint concat uglify`

  Alias to run the `lint`, `concat` and `uglify` tasks. Lints JS, combines `src` JS files & uglifies the output

### `build:images`
  `run-s imagemin icons`

  Alias to run the `imagemin` and `icons` tasks. Compresses images, generates an SVG sprite from a folder of separate SVGs

### `build`
  `run-s build:*`

  Alias to run all of the `build` commands

### `watch:css`
  `onchange 'src/**/*.scss' -- run-s build:css`

  Watches for any .scss file in `src` to change, then runs the `build:css` task

### `watch:js`
  `onchange 'src/**/*.js' -- run-s build:js`

  Watches for any .js file in `src` to change, then runs the `build:js` task

### `watch:images`
  `onchange 'src/images/**/*' -- run-s build:images`

  Watches for any images in `src` to change, then runs the `build:images` task

### `watch`
  `run-p serve watch:*`

  Run the following tasks simultaneously: `serve`, `watch:css`, `watch:js` & `watch:images`. When a .scss or .js file changes in `src` or an image changes in `src/images`, the task will compile the changes to `dist`, and the server will be notified of the change. Any browser connected to the server will then inject the new file from `dist`

### `postinstall`
  `run-s build watch`

  Runs `watch` after `npm install` is finished

## Description
Als User möchte ich täglich und unkompliziert die aktuellsten nachrichten hören und als feed auf der Startseite finden. 
Für weitere Recherche wären Metadaten und Verlinkungen zum Artikeln Sinnvoll.
