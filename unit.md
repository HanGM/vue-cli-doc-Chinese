# 单元测试

先看看这个模板可以使用哪些单元测试模板：

- [Karma](https://karma-runner.github.io/): 启动浏览器来跑测试，运行测试用例并将结果报告给我们。
- [karma-webpack](https://github.com/webpack/karma-webpack): 使用webpack来跑Karma测试的插件
- [Mocha](https://mochajs.org/): 我们编写测试规范的测试框架。
- [Chai](http://chaijs.com/): 提供更好的断言语法的测试断言库。
- [Sinon](http://sinonjs.org/): 测试工具库，提供了spies, stubs 和 mocks。

Chai 和 Sinon是在[karma-sinon-chai](https://github.com/kmees/karma-sinon-chai)中集成的, 所有 Chai 接口 (`should`, `expect`, `assert`) 和 `sinon` 在测试文件中是针对全局生效的。

添加文件:

- `index.js`

  这个是`karma-webpack`的入口文件，可以绑定所有的测试代码与源代码（以达到覆盖的目的）。你可以忽略它的大部分。

- `specs/`

  这是你编写实际测试用例的目录。你可以在你的测试用例中全部使用es2015的写法，同时webpack的loader全部被支持。

- `karma.conf.js`

  Karma配置文件。在 [Karma 文档](https://karma-runner.github.io/)中查看更多细节。

## 在更多浏览器中运行测试

通过安装更多的[karma launchers](https://karma-runner.github.io/1.0/config/browsers.html)和在`test/unit/karma.conf.js`文件中配置`browsers`字段，你可以在多个真实浏览器中运行测试。

## Mocking依赖

本模板默认安装[inject-loader](https://github.com/plasticine/inject-loader)。要通过`*.vue`组件使用的话，去看看[vue-loader模拟测试文档](http://vue-loader.vuejs.org/en/workflow/testing-with-mocks.html)。
