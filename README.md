# webpack-config

## Create Git Repo

```bash
git init
```

go to ur github account and create repo and copy past the commands thats gives to u

## NPM

run

```bash
npm init -y
```

## webpack initail setup

```bash
npm i -D webpack webpack-cli webpack-dev-server
```

then create entry point `src/index.js`

and added the `webpack.config.js` file to the root path

```bash
# ./webpack.config.js
module.exports = {
  mode: 'development',

  devtool: false,
  devServer: {
    contentBase: './dist',
  },
}
```

## Babel

added babel

```bash
npm i -D babel-loader @babel/core @babel/preset-env
```

then add this to `webpack.config.js` file

```bash
module: {
  rules: [
    {
      test: /\.js$/,
      exclude: /node_modules/,
      use: {
        loader: 'babel-loader',
        # options: {
        #   presets: [
        #     ['@babel/preset-env', { targets: "defaults" }]
        #   ]
        # }
      }
    }
  ]
}
```

you can uncomment the presets in the code above or
create file `babel.config.js` then add

```bash
# ./babel.config.js
module.exports = {
  presets: ['@babel/preset-env'],
}
```

## CSS-PostCSS-SASS-HMR

```bash
npm i -D css-loader mini-css-extract-plugin
npm i -D postcss postcss-preset-env postcss-loader
npm i -D sass sass-loader
```

in `webpack.config.js` file add

```bash
const MiniCssExtractPlugin = require('mini-css-extract-plugin')
```

then add rule for mini-css-extract-plugin and css-loader

```bash
module.exports = {
  module: {
    rules: [
      {
        test: /\.s?css$/i,
        use: [
          MiniCssExtractPlugin.loader,
          'css-loader',
          'postcss-loader',
          'sass-loader',
        ],
      },
    ],
  },

  plugins: [new MiniCssExtractPlugin()],
};
```

create file `postcss.config.js` then add

```bash
# ./postcss.config.js
module.exports = {
  plugins: ['postcss-preset-env'],
}
```

## Browserslists

in root dir add file `.browserslistrc`

```bash
# ./.browserslistrc
last 2 versions
> 0.5%
IE 10
```

there is a bug happen in live-reload so add a taregt in `webpack.config.js` file

```bash
# ./webpack.config.js
let target = process.env.NODE_ENV === 'production' ? 'browserslist' : 'web'

module.exports = {
  target,
}
```
