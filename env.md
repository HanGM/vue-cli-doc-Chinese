# 环境变量

有时根据程序运行环境的不同而有不同的配置值是很实际的。

例如:

```js
// config/prod.env.js
module.exports = {
  NODE_ENV: '"production"',
  DEBUG_MODE: false,
  API_KEY: '"..."' // 这是所有环境之间共享的
}

// config/dev.env.js
module.exports = merge(prodEnv, {
  NODE_ENV: '"development"',
  DEBUG_MODE: true // 在prod.env中会覆盖debug_mode值
})

// config/test.env.js
module.exports = merge(devEnv, {
  NODE_ENV: '"testing"'
})
```

> **注意:** 字符串变量需要包成单引号和双引号 `'"..."'`

因此，环境变量是：
- 生产环境
    - NODE_ENV   = 'production',
    - DEBUG_MODE = false,
    - API_KEY    = '...'
- 开发环境
    - NODE_ENV   = 'development',
    - DEBUG_MODE = true,
    - API_KEY    = '...'
- 测试环境
    - NODE_ENV   = 'testing',
    - DEBUG_MODE = true,
    - API_KEY    = '...'

可以看到, `test.env` 继承自 `dev.env`， `dev.env` 继承自 `prod.env`。

### 用法

在代码中使用环境变量很简单。例如:

```js
Vue.config.debug = process.env.DEBUG_MODE
```