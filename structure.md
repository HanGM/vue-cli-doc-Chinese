# 项目结构

``` bash
.
├── build/                      # webpack 配置文件
│   └── ...
├── config/                     
│   ├── index.js                # 项目核心配置
│   └── ...
├── src/
│   ├── main.js                 # 程序入口文件
│   ├── App.vue                 # 程序入口vue组件
│   ├── components/             # 组件
│   │   └── ...
│   └── assets/                 # 模块资源 (会被webpack处理)
│       └── ...
├── static/                     # 纯静态资源 (直接拷贝到dist/static/里面)
├── test/
│   └── unit/                   # 单元测试
│   │   ├── specs/              # 测试规范
│   │   ├── index.js            # 测试入口文件
│   │   └── karma.conf.js       # 测试运行配置文件
│   └── e2e/                    # 端到端测试
│   │   ├── specs/              # 测试规范
│   │   ├── custom-assertions/  # 端到端测试自定义断言
│   │   ├── runner.js           # 运行测试的脚本
│   │   └── nightwatch.conf.js  # 运行测试的配置文件
├── .babelrc                    # babel 配置文件
├── .editorconfig               # 编辑配置文件
├── .eslintrc.js                # eslint 配置文件
├── index.html                  # index.html 入口模板文件
└── package.json                # 运行的脚本与相关依赖
```

### `build/`

这个目录包含实际为开发环境与生产环境的webpack配置文件。通常你不需要关注这些文件，除非你想自定义webpack的loader，这样的话，你应当先看看`build/webpack.base.conf.js`这个文件。

### `config/index.js`

这个是主要的配置文件，会展示大部分在构建步骤中的通用配置。在 [开发环境代理api](proxy.md) 与 [集成后端框架](backend.md) 查看更多细节。

### `src/`

这个是你放大部分程序代码的地方。如何管理这个目录内的所有内容结构在绝大部分程度上取决于你；如果你使用Vuex，你可以瞅瞅[Vuex应用建议](http://vuex.vuejs.org/en/structure.html)。

### `static/`

这个目录是你不想通过webpack处理的静态资源目录。这些目录中的资源会在webpack构建的时候，被直接复制到相同的目录中。

在 [静态资源处理](static.md) 中查看更多细节。

### `test/unit`

包含单元测试相关文件，在[单元测试](unit.md) 中查看更多细节。

### `test/e2e`

包含端到端测试相关文件，在[端到端测试](e2e.md) 中查看更多细节。

### `index.html`

这个是咱们单界面应用中的 **模板** `index.html`。在开发环境中，webpack会生成相关资源，这些资源的url会自动插入到模板来渲染最终的HTML。

### `package.json`

NPM包元数据文件，包括所有的构建依赖与[构建命令](commands.md)。
