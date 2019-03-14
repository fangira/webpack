# 简单配置
[官网文档](https://www.webpackjs.com/guides/getting-started/)

- 安装最新版本和脚手架：
```
npm install --save-dev webpack webpack-cli
```
- 文件布局
```
webpack-demo
|- package.json
|- webpack.config.js
|- /dist //整个文件夹都是自动生成的
  |- bundle.js
  |- index.html
|- /src
  |- index.js //入口文件
  |- index.html //HTML模板
|- /node_modules
```
- 在package.json添加命令（npm init创建）

```js
// package.json 
"scripts": {
    "build": "webpack"
}
```
- webpack.config.js

```js
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin'); // 通过 npm 安装 npm i html-webpack-plugin --save-dev
const webpack = require('webpack'); // 用于访问内置插件
module.exports = {
    entry: './src/index.js',
    output: {
        filename: 'bundle.js',
        path: path.resolve(__dirname, 'dist')
    },
    module: {
        rules: [
            { test: /\.txt$/, use: 'raw-loader' }
        ]
    },
    plugins: [
        new HtmlWebpackPlugin({ template: './src/index.html' })
    ]
};
```

- 执行

```
npm run build
```
