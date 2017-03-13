# SEO预渲染

如果你想预渲染路由，并且这些路由一旦推送到生产环境后不会明显改变，使用这个webpack插件：[prerender-spa-plugin](https://www.npmjs.com/package/prerender-spa-plugin)，这个已经被Vue使用并测试通过。对于那些有频繁改变的界面，[Prerender.io](https://prerender.io/) 和 [Netlify](https://www.netlify.com/pricing)都会有规律的为搜索引擎来预渲染你的内容。

## 使用 `prerender-spa-plugin`

1. 当做一个开发依赖安装它

```bash
npm install --save-dev prerender-spa-plugin
```

2. 在 **build/webpack.prod.conf.js** 中引入：

```js
// 这一句需要放到其余'imports'引入文件的最顶部
var PrerenderSpaPlugin = require('prerender-spa-plugin')
```

3. 在`plugins`数组中配置(在 **build/webpack.prod.conf.js** 里面也需要配置):

```js
new PrerenderSpaPlugin(
  // 编译项目工程的路径
  path.join(__dirname, '../dist'),
  // List of endpoints you wish to prerender
  // 你想要预渲染的端点列表
  [ '/' ]
)
```

如果你还想预渲染`/about`和`/contact`目录，那么这个数组应当是`[ '/', '/about', '/contact' ]`。