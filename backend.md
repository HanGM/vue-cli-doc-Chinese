# 集成后端框架

如果你正在建设一个纯静态的应用程序（与后端api分离部署），那么你可能甚至不需要编辑`config/index.js`。但是，如果你想要这个模板与现有的后端框架集成，例如Rails/Django/Laravel，拥有自己的项目结构，您可以编辑`config/index.js`，直接生成前端资源注入到你的后台项目。

让我们看一下默认的`config/index.js`:

``` js
var path = require('path')

module.exports = {
  build: {
    index: path.resolve(__dirname, 'dist/index.html'),
    assetsRoot: path.resolve(__dirname, 'dist'),
    assetsSubDirectory: 'static',
    assetsPublicPath: '/',
    productionSourceMap: true
  },
  dev: {
    port: 8080,
    proxyTable: {}
  }
}
```

在'build'部分，我们有以下选项：

### `build.index`

> 必须是本地文件系统上的绝对路径。

`index.html` (带着插入的资源路径) 会被生成。

如果你在后台框架中使用此模板，你可以编辑`index.html`路径指定到你的后台程序生成的文件。例如Rails程序，可以是`app/views/layouts/application.html.erb`，或者Laravel程序，可以是`resources/views/index.blade.php`。

### `build.assetsRoot`

> 必须是本地文件系统上的绝对路径。

应该指向包含应用程序的所有静态资产的根目录。`public/` 对应Rails/Laravel。

### `build.assetsSubDirectory`

被webpack编译处理过的资源文件都会在这个`build.assetsRoot`目录下，所以它不可以混有其它可能在`build.assetsRoot`里面有的文件。例如，假如`build.assetsRoot`参数是`/path/to/dist`，`build.assetsSubDirectory` 参数是 `static`, 那么所以webpack资源会被编译到`path/to/dist/static`目录。

每次编译前，这个目录会被清空，所以这个只能放编译出来的资源文件。

`static/`目录的文件会直接被在构建过程中，直接拷贝到这个目录。这意味着是如果你改变这个规则，所有你依赖于`static/`中文件的绝对地址，都需要改变。在 [处理静态资源](static.md) 中查看更多细节。

### `build.assetsPublicPath`

这个是通过http服务器运行的url路径。在大多数情况下，这个是根目录(`/`)。如果你的后台框架对静态资源url前缀要求，你仅需要改变这个参数。在内部，这个是被webpack当做`output.publicPath`来处理的。

### `build.productionSourceMap`

在构建生产环境版本时是否开启source map。

### `dev.port`

开发服务器监听的特定端口

### `dev.proxyTable`

定义开发服务器的代理规则。在 [开发环境代理api](proxy.md) 文档中查看更多细节。
