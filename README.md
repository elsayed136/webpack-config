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
module.exports = {
  presets: ['@babel/preset-env'],
}
```
