# JavaScript

```js
mix.js(src|[src], output)
```

With a single line of code, Webpack Mix allows you to trigger a number of vital actions.

* ES2017 + modules compilation
* Build and compile `.vue` components \(via `vue-loader`\)
* Hot module replacement
* Tree-shaking, new in webpack 2 \(removes unused library code\)
* Extract vendor libraries \(via `mix.extract()`\), for improved long-term caching
* Automatic versioning \(query string hash\), via `mix.version()`


### Usage

```js
let mix = require('webpack-mix').mix;

// 1. A single src and output path.
mix.js('src/app.js', 'dist/app.js');


// 2. For additional src files that should be 
// bundled together:
mix.js([
    'src/app.js',
    'src/another.js'
], 'dist/app.js');


// 3. For multiple entry/output points:
mix.js('src/app.js', 'dist/')
   .js('src/forum.js', 'dist/');
```


### React Support

Laravel Mix also ships with basic React support. Simply update your `mix.js()` call to `mix.react()`, and then use the exact same set of arguments. Behind the scenes, Mix will pull in and reference any necessary Babel plugins for React.

```js
mix.react('resources/assets/js/app.jsx', 'public/js/app.js');
```

Of course, you'll still want to install React and ReactDOM through NPM, per usual, but everything else should be taken care of.
