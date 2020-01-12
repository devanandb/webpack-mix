# Installation

Webpack Mix can be used for any type of application.

### Project

Begin by installing Webpack Mix through NPM or Yarn, and then copying the example Mix file to your project root.

```bash
mkdir my-app && cd my-app
npm init -y
npm install webpack-mix --save-dev
cp node_modules/webpack-mix/setup/webpack.mix.js ./
```

You should now have the following directory structure:

-   `node_modules/`
-   `package.json`
-   `webpack.mix.js`

`webpack.mix.js` is your configuration layer on top of webpack. Most of your time will be spent here.

Head over to your webpack.mix.js file:

```js
let mix = require('webpack-mix');

mix.js('src/app.js', 'dist')
    .sass('src/app.scss', 'dist')
    .setPublicPath('dist');
```

Take note of the source paths. You're free to amend the paths to match your preferred structure, but if you're happy with our defaults simply run `mkdir src && touch src/app.{js,scss}` to create the files/directories. You're all set now. Compile everything down by running `node_modules/.bin/webpack` from the command line. You should now see:

-   `dist/app.css`
-   `dist/app.js`
-   `dist/mix-manifest.json` (Your asset dump file, which we'll discuss later.)

Nice job! Now get to work on that project.

#### NPM Scripts

As a tip, consider adding the following NPM scripts to your `package.json` file, to speed up your workflow.

```js
  "scripts": {
    "dev": "NODE_ENV=development node_modules/webpack/bin/webpack.js --progress --hide-modules --config=node_modules/webpack-mix/setup/webpack.config.js",
    "watch": "NODE_ENV=development node_modules/webpack/bin/webpack.js --watch --progress --hide-modules --config=node_modules/webpack-mix/setup/webpack.config.js",
    "hot": "NODE_ENV=development webpack-dev-server --inline --hot --config=node_modules/webpack-mix/setup/webpack.config.js",
    "production": "NODE_ENV=production node_modules/webpack/bin/webpack.js --progress --hide-modules --config=node_modules/webpack-mix/setup/webpack.config.js"
  }
```
