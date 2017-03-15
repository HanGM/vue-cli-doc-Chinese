## vue-cli webpack模板中文文档

> 译者：楼兰一剑——乐视云计算大前端组  

> [本文gitbook地址查阅](https://loulanyijian.github.io/vue-cli-doc-Chinese/)

> 译者注：要本地查看本教程，需要npm全局安装gitbook —— clone到本地 —— gitbook install —— gitbook serve

> 原文参考：[vue-cli](https://github.com/vuejs/vue-cli)、[英文文档](http://vuejs-templates.github.io/webpack)


本模板针对的是比较大的、严谨的项目，并且默认你对 Webpack 和 `vue-loader`熟悉。不过这也要读一下[`vue-loader`文档（中文-同为本文译者翻译）](https://loulanyijian.github.io/vue-loader-doc-Chinese/)来确保熟悉常见的工作流程。

如果你只是想要试着玩一下`vue-loader`或者鼓捣一个快速原型，可以试试使用这个简易的[webpack-simple](https://github.com/vuejs-templates/webpack-simple)模板代替（这个简易模板里可以配置的东西比较少，最终的项目还是会使用这个标准webpack模板的——**译者注**）。

## 快速启动

要使用本模板，需要使用[vue-cli](https://github.com/vuejs/vue-cli)脚手架工具。**建议使用NPM 3 +来加载更多依赖**。

``` bash
$ npm install -g vue-cli
$ vue init webpack my-project
$ cd my-project
$ npm install
$ npm run dev
```
