# JavaScript

```js
mix.js(src|[src], output)
```

With a single line of code, Webpack Mix allows you to trigger a number of vital actions.

* ES2015 + modules compilation
* Hot module replacement
* Tree-shaking, new in Webpack 2 \(removes unused library code\)
* Extract vendor libraries \(via `mix.extract()`\), for improved long-term caching
* Automatic versioning \(file hashing\), via `mix.vendor()`


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
