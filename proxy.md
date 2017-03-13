# 开发环境代理api

当使用此模板与一个已经存在的后台配合开发时，一般需要在开发环境下访问后台的API。要做到这一点，我们可以使开发服务器和后台api并行运行（或远程运行），并让开发服务器代理的所有实际后台的API请求。

要配置代理规则，编辑`config/index.js`文件中的`dev.proxyTable`选项。开发服务器使用[http代理中间件](https://github.com/chimurai/http-proxy-middleware) 来做代理，所以你应当瞅瞅它的文档来查看细节使用。不过这里有个简单的例子：

``` js
// config/index.js
module.exports = {
  // ...
  dev: {
    proxyTable: {
      // 代理所有以/api开始的请求到jsonplaceholder
      '/api': {
        target: 'http://jsonplaceholder.typicode.com',
        changeOrigin: true,
        pathRewrite: {
          '^/api': ''
        }
      }
    }
  }
}
```

上面的例子会将`/api/posts/1`请求代理到`http://jsonplaceholder.typicode.com/posts/1`上。

## 匹配URL

除了静态的URL，您也可以使用glob模式匹配URL，例如`/api/**`在 [上下文匹配](https://github.com/chimurai/http-proxy-middleware#context-matching)。另外，你可以提供一个`filter`选项，可以自定义函数来确定请求是否应该被代理：

``` js
proxyTable: {
  '*': {
    target: 'http://jsonplaceholder.typicode.com',
    filter: function (pathname, req) {
      return pathname.match('^/api') && req.method === 'GET'
    }
  }
}
```
