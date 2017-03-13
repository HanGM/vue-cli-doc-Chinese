# 静态资源处理

你会注意到在项目结构上我们有静态资源两个目录：`src/assets` 和 `static/`。它们之间有什么区别？

### 通过webpack处理的资源

要回答这个问题，我们首先需要了解webpack如何处理静态资源。在`*.vue`组件中，你所有的html模板和CSS都会被`vue-html-loader` 和 `css-loader`压缩并且查找资源路径。例如，`<img src="./logo.png">` 和 `background: url(./logo.png)`，`"./logo.png"`是一个相对路径的资源文件，会**被webpack处理成一个模块依赖**。

因为`logo.png`不是JavaScript，当要视为一个模块的依赖时，我们需要使用`url-loader` 和 `file-loader`来处理。这个模板已经给你配置了这些loader，所以你可以轻易得到如指纹文件和Base64内联的功能，同时能够使用相对路径，从而不必担心部署。

因为这些资源可能会在构建过程中被内联/复制/重命名，它们本质上还是你的一部分源代码。这就是为什么建议要将通过webpack处理的静态资源放置到`/src`目录、与其余的源代码放在相同的地方。实际上，你甚至都不必将它们放置到`/src/assets`文件夹中：你可以把他们放到具体的 模块/组件 目录中来使用。例如，你可以将每一个组件放到它们自己的目录中，靠着它们的静态资源。

### 资源处理规则

- **相对路径url**, 例如 `./assets/logo.png` 会注入到一个模块依赖中。他们会基于你webpack输出配置，自动替换生成的URL。

- **无前缀的url**, 例如 `assets/logo.png` 会被视为相同的相对路径url，被编译进`./assets/logo.png`。

- **带有`~`前缀的url** 会作为一个模块的请求, 类似于 `require('some-module/image.png')`。如果你希望当做一个模块来处理，你就需要使用这个前缀。例如你有一个`assets`的别名需要处理, 你需要使用`<img src="~assets/logo.png">` 来确认别名被注意到。

- **根目录相对路径**, 例如 `/assets/logo.png` 直接不支持这种写法。

### 获取JS文件资源路径

为了使webpack返回正确的资源路径，你需要使用`require('./relative/path/to/file.jpg')`，这样的话会通过`file-loader`处理并返回处理过的url路径。例如：

``` js
computed: {
  background () {
    return require('./bgs/' + this.id + '.jpg')
  }
}
```

**注意上面的例子会将`./bgs/`目录下的每个图片最后生成**。这是因为webpack猜不到它们哪个会在运行时会被使用，所以它会生成所有的文件。

### "真的"静态资源

相比之下，在`static/`并非由Webpack来处理：他们是以相同的文件名，直接复制到他们的最终目标目录。你必须关注这些文件使用绝对路径，这个通过`config.js`文件中的 `build.assetsPublicPath` 和 `build.assetsSubDirectory`来控制。

如下面的例子，会有如下的默认值

``` js
// config.js
module.exports = {
  // ...
  build: {
    assetsPublicPath: '/',
    assetsSubDirectory: 'static'
  }
}
```

任何放置在`static/`的文件都使用绝对的URL `/static/[filename]`来引用。如果你修改`assetSubDirectory` 参数成 `assets`，然后这些URL需要变成`/assets/[filename]`。

我们将在[后端集成](backend.md)中学习到更多关于配置文件的内容。
