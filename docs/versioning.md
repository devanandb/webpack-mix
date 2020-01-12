# Versioning

```js
mix.js('src', 'output').version([]);
```

To assist with long-term caching, Webpack Mix provides the `mix.version()` method, which enables file hashing. such as `app.js?id=8e5c48eadbfdd5458ec6`. This is useful for cache-busting. Imagine that your server automatically caches scripts for a year, to improve performance. That's great, but, each time you make a change to your application code, you need some way to instruct the server to bust the cache. This is typically done through the use of query strings, or file hashing.

With versioning enabled, each time your code changes, a new hashed query string file will be generated. Consider the following `webpack.mix.js` file.

```js
let mix = require('webpack-mix');

mix.js('resources/assets/js/app.js', 'public/js')
    .sass('resources/assets/sass/app.sass', 'public/css')
    .version();
```

Upon compilation, you'll see `/css/app.css?id=5ee7141a759a5fb7377a` and `/js/app.js?id=0441ad4f65d54589aea5` in your `mix-manifest.json` file. Of course, your particular hash will be unique. Each time you adjust your JavaScript, the compiled files will receive a newly hashed name, which will effectively bust the cache, once pushed to production.

As an example, try running`webpack --watch`, and then change a bit of your JavaScript. You'll instantly see a newly generated bundle and stylesheet.

### Importing Versioned Files

This all begs the question: how exactly do we include these versioned scripts and stylesheets into your HTML, if the names keep changing? Yes, that can be tricky. The answer will be dependent upon the type of application you're building. For SPAs, you may dynamically read Webpack Mix's generated `manifest.json` file, extract the asset file names \(these will be updated for each compile to reflect the new versioned file\), and then generate your HTML.

### Versioning Extra Files

The `mix.version()` will automatically version any compiled JavaScript, Sass/Less, or combined files. However, if you'd also like to version extra files as part of your build, simply pass a path, or array of paths, to the method, like so:

```js
mix.version(['public/js/random.js']);
```

Now, we'll still version any relevant compiled files, but we'll also append a query string, `public/js/random.js?{hash}`, and update your `mix-manifest.json` file.
