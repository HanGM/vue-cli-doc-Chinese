# 构建命令

所有的构建命令，都会通过[NPM脚本](https://docs.npmjs.com/misc/scripts)执行。

### `npm run dev`

> 启动一个Node.js本地开发服务器。在 [开发环境代理api](proxy.md)中查看更多细节。

- Webpack + `vue-loader` 来处理Vue单文件组件
- 状态支持热更新
- 状态支持浮层显示编译错误
- 在保存的时候，通过ESLint做语法检测
- 可以开启Source maps

### `npm run build`

> 构建生产环境的资源. 在 [整合后端框架](backend.md) 查看更多细节.

- 通过 [UglifyJS](https://github.com/mishoo/UglifyJS2) 压缩JS文件。
- 通过 [html-minifier](https://github.com/kangax/html-minifier)来压缩html文件。
- 通过 [cssnano](https://github.com/ben-eb/cssnano)，提取出所有组件内的css文件，合并压缩到一个单独的文件。
- 所有的静态资源会编译成哈希值版本来保持长期缓存，生成环境的`index.html`会自动插入这些编译后资源文件的url。
- 你也可以在[部署纪要](http://vuejs-templates.github.io/webpack/commands.html#how-do-i-deploy-built-assets-with-my-backend-framework)中查看。

### `npm run unit`

> 通过 [Karma](https://karma-runner.github.io/)，在PhantomJS上运行单元测试。在 [单元测试](unit.md) 中查看更多细节。

- 在测试文件中支持ES2015
- 支持所有的webpack loader
- 轻松 [注入测试](http://vuejs.github.io/vue-loader/en/workflow/testing-with-mocks.html)。

### `npm run e2e`

> 通过 [Nightwatch](http://nightwatchjs.org/)运行端到端测试。在[端到端测试](e2e.md) 中查看更多细节.

- 在多个浏览器中并行运行测试
- 通过盒子里的一个命令工作。
  - 自动处理 `Selenium` 和 `chromedriver` 依赖.
  - 自动创建 `Selenium` 服务器.
