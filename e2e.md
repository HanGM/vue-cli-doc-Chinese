# 端到端测试

本模板使用的是[Nightwatch.js](http://nightwatchjs.org)来做端到端测试。Nightwatch.js是一个高度集成到Selenium的端到端测试。本模板为你带来了Selenium服务器和chromedriver二进制文件的预配置，所以你不需要管这部分。

让我们看一下 `test/e2e` 目录的文件吧：

- `runner.js`

  运行一个开发服务器的nodejs脚本，可以在上面跑Nightwatch。这是你运行`npm run e2e`时运行的脚本。

- `nightwatch.conf.js`

  Nightwatch配置文件。在 [Nightwatch's 配置文件](http://nightwatchjs.org/guide#settings-file) 中查看更多细节。

- `custom-assertions/`

  可用于Nightwatch测试的自定义断言。在 [Nightwatch's 编写自定义断言文档](http://nightwatchjs.org/guide#writing-custom-assertions) 中查看更多细节。

- `specs/`

  你的实际测试用例! 在 [Nightwatch'编写测试用例文档](http://nightwatchjs.org/guide#writing-tests) 和 [API 参考](http://nightwatchjs.org/api) 中查看更多细节。

### 在更多浏览器中运行测试用例

要配置浏览器来运行测试，需要在[`test/e2e/nightwatch.conf.js`](https://github.com/vuejs-templates/webpack/blob/master/template/test/e2e/nightwatch.conf.js#L17-L39)文件中的"test_settings"添加一个入口，还需要在运行[`test/e2e/runner.js`](https://github.com/vuejs-templates/webpack/blob/master/template/test/e2e/runner.js#L15)脚本时添加`--env`标签。如果你想像SauceLabs一样配置服务器上的远程测试，你可以基于环境变量的条件修改Nightwatch的配置，或使用一个单独的配置文件。在[Nightwatch's docs on Selenium](http://nightwatchjs.org/guide#selenium-settings)中查询更多细节。
