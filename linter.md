# 编程风格配置

这个样板使用[ESLint](http://eslint.org/)为风格控制，并使用如下[标准](https://github.com/feross/standard/blob/master/rules.md)预设一些小的风格。

如果你对默认的风格规则不爽，你可以通过以下几种方式自定义：

1. 在`.eslintrc.js`文件中重写个人规则。例如，你可以添加以下规则执行保留分号而不是忽略它们:

  ``` js
  "semi": [2, "always"]
  ```

2. 在生成项目的时候，选择一个不同的ESLint预设, 例如：[eslint-config-airbnb](https://github.com/airbnb/javascript/tree/master/packages/eslint-config-airbnb)。

3. 在生成项目的时候，不选择ESLint预设而定义自己的规则。在 [ESLint文档](http://eslint.org/docs/rules/) 中查看更多细节。
