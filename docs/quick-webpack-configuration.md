# Quick Webpack Configuration

```js
 mix.webpackConfig({});
```

While, of course, you're free to edit the provided `webpack.config.js` file, in certain settings, it's easier to modify or override the default settings directly from your `webpack.mix.js` file. 

As an example, perhaps you want to add a custom array of modules that should be automatically loaded by webpack. You have two options in this scenario:

1. Edit your `webpack.config.js` file, as needed.
2. Call `mix.webpackConfig()` within your `webpack.mix.js` file, and pass your overrides. Mix will then perform a deep merge.


## Using a Callback Function

You can access webpack and all of its properties when passing a callback function.

```js
mix.webpackConfig(webpack => {
    return {
        plugins: [
            new webpack.ProvidePlugin({
                $: 'jquery',
                jQuery: 'jquery', 
                'window.jQuery': 'jquery',
            })
        ]
    };
});
```


