# 简单配置
[官网文档](https://www.webpackjs.com/guides/getting-started/)

- 安装最新版本和脚手架：
```
npm install --save-dev webpack webpack-cli webpack-dev-server html-webpack-plugin url-loader style-loader css-loader
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
    "build": "webpack",
    "dev":"node_modules/.bin/webpack-dev-server"
}
```
- webpack.config.js(修改js入口，HTML模板入口即可)

```js
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');
const webpack = require('webpack'); // 用于访问内置插件
module.exports = {
    mode: "development",
    entry: './jq/js/index.js',
    output: {
        filename: 'bundle.js',
        path: path.resolve(__dirname, 'dist')
    },
    module: {
        rules: [
            {
                test: /\.css$/,
                use: ['style-loader', 'css-loader']
            },
            {
                test: /\.(png|jpg|gif)$/,
                use: [
                    {
                        loader: 'url-loader',
                        options: {
                            limit: 8192
                        }
                    }
                ]
            }
        ]
    },
    plugins: [
        new HtmlWebpackPlugin({ template: './jq/index.html' })
    ],
    devServer: {
        contentBase: path.join(__dirname, "dist"),
        compress: true,
        port: 9000,
        host: '0.0.0.0' //
    }
};
```

- 执行

```
npm run dev
```
