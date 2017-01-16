# Hot Module Replacement

Where available, Webpack Mix provides seamless support for hot module replacement.

> Hot Module Replacement \(or Hot Reloading\) allows you to, not just refresh the page when a piece of JavaScript is changed, but it will also maintain the current state of the component in the browser. As an example, consider a simple counter component. When you press a button, the count goes up. Imagine that you click this button a number of times, and then update the component file. Once you do, the webpage will refresh to reflect your change, but the count will remain the same. It won't reset. This is the beauty of hot reloading!

### Usage

Have a look at your  `package.json` file. Within the `scripts` object, you'll see:

```js
  "scripts": {
    "webpack": "cross-env NODE_ENV=development webpack --progress --hide-modules",
    "dev": "cross-env NODE_ENV=development webpack --watch --progress --hide-modules",
    "hmr": "cross-env NODE_ENV=development webpack-dev-server --inline --hot",
    "production": "cross-env NODE_ENV=production webpack --progress --hide-modules"
  }
```

Take note of the `hmr` option; this is the one you want. From the command line, run `npm run hmr` to boot up a Node server and monitor your bundle for changes. Next, load your app in the browser, as you normally would. Perhaps, `http://my-app.dev`.

The key to making hot reloading work within an application is ensuring that all script sources reference the Node server URL that we just booted up. This will be [http://localhost:8080](http://localhost:8080). Now you could of course manually update your HTML files, like so:

```html
<body>
    <div id="app">...</div>
    <script src="http://localhost:8080/js/bundle.js"></script>
</body>
```


### Usage in SPAs

Webpack Mix includes many popular loaders package, which means, for SPAs, there's nothing for you to do. It'll all work seamlessly out of the box!

