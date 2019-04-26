# Webpack and Babel

## Starting off

### Making the stuff

Make a folder for your project, and in there make a folder called `src` for files.
`npm init -y`
In your package.js under scripts, add the build and start script: 

```json
"scripts": {
  "build": "webpack-cli --mode production --entry ./src/index.js --output ./dist/bundle.js",
  "start:dev": "webpack-dev-server --entry ./src/index.js --output ./dist/bundle.js"
}
```
Now for all the packages

```bash
npm i webpack webpack-cli webpack-dev-server @babel/core babel-loader @babel/preset-env html-webpack-plugin html-loader --save-dev
```

If you're doing react, add `react react-dom @babel/preset-react`

`preset-env` compiles es2016+ to es15
`preset-react` compiles jsx to normal js

The transformation is called transpiling. Webpack doesn’t know how to transform ES6 JavaScript to ES5 but it has this concept of loaders: think of them as of transformers. A webpack loader takes something as the input and produces something else as the output.

babel-loader is the Webpack loader responsible for taking in the ES6 code and making it understandable by the browser of choice.

### Creating the config

#### .babelrc
Create a `.babelrc` and put in this code for the loaders
```json
{
  "presets": ["@babel/preset-env", "@babel/preset-react"]
}
```
Get rid of the react one if you don't need it.

#### webpack.config.js

If you're doing react with a webpage

```js
const HtmlWebPackPlugin = require("html-webpack-plugin");
module.exports = {
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: {
          loader: "babel-loader"
        }
      },
      {
        test: /\.html$/,
        use: [
          {
            loader: "html-loader"
          }
        ]
      }
    ]
  },
  plugins: [
    new HtmlWebPackPlugin({
      template: "./src/index.html",
      filename: "./index.html"
    })
  ]
};
```

Without the jsx check, it can be without react too.

Without the html stuff it's:

```js
module.exports = {
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: {
          loader: "babel-loader"
        }
      }
    ]
  }
};
```
## More stuff

If you're doing react, you probably want to import css to use to, which need to be bundled too.
For that, install `npm install --save-dev style-loader css-loader`
Now in webpack config:
```json
   module: {
     rules: [
       {
         test: /\.css$/,
         use: [
           'style-loader',
           'css-loader'
         ]
       }
     ]
   }
```

For files and pictures, we have file-loader:
`npm install --save-dev file-loader`
In webpack config:
```json
       {
         test: /\.(png|svg|jpg|gif)$/,
         use: [
           'file-loader'
         ]
       }
```
In Pixi.JS, you can import the images as a URL and then when loading resources with PIXI.loader.add, the array items will be an object with the image name and the url.
## What happens

All the files connected to index.js will be bundled as one with `import something from './something.js'` and `export default something` everywhere.
If you install html modules with npm like pixi.js or clientjs, you can import it like that.
Other scripts in the index.html work too.

It's cool
