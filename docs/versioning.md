# Versioning

```js
mix.js('src', 'output')
   .version();
```

To assist with long-term caching, Webpack Mix provides the `mix.version()` method, which enables file name hashing. such as `app.8e5c48eadbfdd5458ec6.js`. This is useful for cache-busting. Imagine that your server automatically caches scripts for a year, to improve performance. That's great, but, each time you make a change to your application code, you need some way to instruct the server to bust the cache. This is typically done through the use of query strings, or file hashing.

With versioning enabled, each time your code changes, a new hashed file will be generated, and the old one will be deleted. Consider the following `webpack.mix.js` file.

```js
let mix = require('webpack-mix').mix;

mix.js('resources/assets/js/app.js', 'public/js');
   .sass('resources/assets/sass/app.sass', 'public/css')
   .version();
```

Upon compilation, you'll see `./public/css/app.8e5c48eadbfdd5458ec6.css` and .`/public/js/app.8e5c48eadbfdd5458ec6.js`. Of course, your particular hash will be unique. Each time you adjust your JavaScript, the compiled files will receive a newly hashed name, which will effectively bust the cache, once pushed to production.

As an example, try running`webpack --watch`, and then change a bit of your JavaScript. You'll instantly see a newly generated bundle and stylesheet.

### Importing Versioned Files

This all begs the question: how exactly do we include these versioned scripts and stylesheets into your HTML, if the names keep changing? Yes, that can be tricky. The answer will be dependent upon the type of application you're building. For SPAs, you may dynamically read Webpack Mix's generated `manifest.json` file, extract the asset file names \(these will be updated for each compile to reflect the new versioned file\), and then generate your HTML.

#### Note

Versioning is only performed when running in `production` mode.  (ie with `NODE_ENV=production`)

