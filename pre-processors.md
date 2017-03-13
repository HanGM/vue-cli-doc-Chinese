# 预处理器

这个模板已经预设设置大部分流行的css预处理器，包括 LESS, SASS, Stylus, 和 PostCSS。要使用一个预处理器的话 ，所有你需要做的就是安装相应的webpack loader。例如，使用SASS:

``` bash
npm install sass-loader node-sass --save-dev
```

你需要安装`node-sass`，因为`saas-loader`需要这个依赖项

### 在组件里面使用预处理器

安装成功后, 你可以通过修改`<style>`标签上的`lang`属性，在你的`*.vue`组件中使用预处理器。

``` html
<style lang="scss">
/* 写 SASS 代码! */
</style>
```

### 使用SASS语法的一个提示

- `lang="scss"` 对应CSS超集语法（用大括号和semicolones）。
- `lang="sass"` 对应缩进语法。

### PostCSS

默认的情况下，在`*.vue`文件中的样式会被PostCSS处理，所以你不需要用一个特殊的loader来操作它。如果你想用它的话，你可以简单的在`build/webpack.base.conf.js`文件中添加PostCSS插件，在`vue`代码块下面。


``` js
// build/webpack.base.conf.js
module.exports = {
  // ...
  vue: {
    postcss: [/* 你的插件 */]
  }
}
```

在 [vue-loader's 相关文档](http://vuejs.github.io/vue-loader/en/features/postcss.html) 中查看更多细节。

### 独立的 CSS 文件

为了确保一致的提取和处理，建议从全局引入，在根组件`App.vue`中引入独立样式文件，例如：
``` html
<!-- App.vue -->
<style src="./styles/global.less" lang="less"></style>
```

注意，你可能只需要为你自己编写的应用程序编写样式。在那些存在的样式库，如Bootstrap 或 Semantic UI，你可以在 `/static`文件夹中放置他们并且直接在`index.html`文件中引入。这样做会避免额外的构建时间，也更好的利用浏览器的缓存。(请参考[处理静态资源](static.md))
