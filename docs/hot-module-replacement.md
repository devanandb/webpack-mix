# Hot Module Replacement

Where available, Webpack Mix provides seamless support for hot module replacement.

> Hot Module Replacement \(or Hot Reloading\) allows you to, not just refresh the page when a piece of JavaScript is changed, but it will also maintain the current state of the component in the browser. As an example, consider a simple counter component. When you press a button, the count goes up. Imagine that you click this button a number of times, and then update the component file. Once you do, the webpage will refresh to reflect your change, but the count will remain the same. It won't reset. This is the beauty of hot reloading!

### Usage on HTTPS

If you develop your app on an HTTPS connection, your hot reloading scripts and styles must also be served via HTTPS. To achieve this, add the `--https` flag to the `hot` option command within `package.json`:

```js
  "scripts": {
    "hot": "NODE_ENV=development webpack-dev-server --inline --hot --https",
  }
```

With the above setting, the `webpack-dev-server` will generate a self-signed certificate for you. If you wish to use your own certificate, you may use these settings:

```js
    "hot": "NODE_ENV=development webpack-dev-server --inline --hot --https --key /path/to/server.key --cert /path/to/server.crt --cacert /path/to/ca.pem",
```

Now, in your HTML/Blade files you can use either:

```html
<script src="https://localhost:8080/js/bundle.js"></script>
```

or:

```html
<script src="{{ mix('js/bundle.js') }}"></script>
```

### Usage in SPAs

Webpack Mix includes the popular `vue-loader` package, which means, for SPAs, there's nothing for you to do. It'll all work seamlessly out of the box!
