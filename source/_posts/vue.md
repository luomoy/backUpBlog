---
title: vue使用打包工具出现黄色警告
data: 2018-05-08
tag: 
	- vue
---
启动vue时遇到的问题

### 浏览器控制台出现黄色警示代码


找到build->webpack.base.config.js。注释或者去掉下面代码

``` java
const createLintingRule = () => ({
  /*test: /\.(js|vue)$/,
  loader: 'eslint-loader',
  enforce: 'pre',
  include: [resolve('src'), resolve('test')],
  options: {
    formatter: require('eslint-friendly-formatter'),
    emitWarning: !config.dev.showEslintErrorsInOverlay
  }*/
})
```

*这是因为你使用 ESLint，用来规范代码风格的。你的 Webpack 配置中大概是使用了 eslint-loader。在多人协作或大项目中推荐使用，不想要就在webpack.config.js 中去掉。eslint是语法检查工具，但限制太过于严格，大部分开发人员无法适应，所以产生这个需求。*

<font color=red>注意只删除和注释/**/内的代码。另外这段也可能在不在createLintingRule中，也可能在module.export中。所以建议直接在webpack.base.config.js搜索eslint-loader。最后记得重跑项目。</font>