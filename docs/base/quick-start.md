# 快速上手

---

> 本节讲介绍如何快速的搭建系统


## # 下载

```bash
git clone http://git.asa/DoMoreDoBetter/ASA-Web-Formwork.git
```

## # 项目结构

```html
|- build/  -------------------------------- webpack构建目录
    |- build.js
    |- check-versions.js
    |- utils.js
    |- vue-loader.conf.js
    |- webpack.base.conf.js  -------------- 基础webpack配置
    |- webpack.dev.conf.js  --------------- 开发环境webpack配置
    |- webpack.prod.conf.js  -------------- 构建生产环境webpack配置
    |- webpack.test.conf.js  -------------- 测试环境webpack配置
|- config/  ------------------------------- env环境变量配置目录
    |- dev.env.js  ------------------------ 开发环env境环境变量配置
    |- index.js  -------------------------- 基础env环境变量配置
    |- prod.env.js  ----------------------- 构建生产环境env环境变量配置
    |- test.env.js  ----------------------- 测试环境env环境变量配置
|- server/  ------------------------------- 开发环境node服务目录
    |- mock/  ----------------------------- mock数据目录
    |- index.js  -------------------------- 开发node环境部署
|- src/  ---------------------------------- 源码目录
    |- api/  ------------------------------ 与后台对接api目录
        |- index.js  ---------------------- API定义
    |- assets/  --------------------------- 需Webpack处理的静态资源目录
    |- business/  ------------------------- 各模块业务相关，接入vuex store modules中
        |- mutation-types.js  ------------- 模块mutation的类型统一管理        
    |- components/  ----------------------- 组件目录
        |- base/  ------------------------- 基础组件目录
        |- layout/  ----------------------- 布局组件目录
    |- event-bus/  ------------------------ 全局事件总线目录
    |- global/  --------------------------- vue的全局directive、filter、mixin以及全局常量目录
    |- locale/  --------------------------- 国际化目录
        |- lang/  ------------------------- 语言目录
            |- zh-CN.js  ------------------ 中文
    |- model/  ---------------------------- 数据模型
    |- router/  --------------------------- 路由
        |- index.js  ---------------------- 路由入口
        |- routes.js  --------------------- 业务路由汇总
    |- services/  --------------------------- 服务
        |- Schema/  ----------------------- Schema封装目录 
        |- Error.js  ---------------------- 错误处理
        |- storage.js  -------------------- storage封装           
        |- routes.js  --------------------- 业务路由汇总
        |- fetch.js  ---------------------- Axios        
    |- store/  ---------------------------- vuex目录
        |- modules/  ---------------------- 框架 store modules
        |- actions.js  -------------------- 全局action定义
        |- getters.js  -------------------- 全局getter定义
        |- index.js  ---------------------- store 入口
        |- mutation-types.js  ------------- 全局mutation的类型统一管理
        |- mutations.js  ------------------ 全局mutations定义
    |- style/  ---------------------------- 全局样式、全局less变量配置目录
    |- utils/  ---------------------------- 工具库目录
        |- assist.js  --------------------- 帮助函数
        |- env.js  ------------------------ 客户端环境监测
    |- validate/  ------------------------- 验证器目录
    |- views/  ---------------------------- 视图目录
        |- components/  ------------------- 业务通用组件目录
        |- error/  ------------------------ 错误视图目录
        |- home/  ------------------------- 首页视图
        |- layout/  ----------------------- 框架视图
        |- login/  ------------------------ 登录视图
|- static/ -------------------------------- 无需Webpack处理的静态资源目录
|- test/ ---------------------------------- 测试目录
    |- unit/  ----------------------------- 单元测试目录
        |- specs/  ------------------------ 测试脚本目录
        |- .eslintrc  --------------------- 单元测试eslint配置目录        
        |- index.js  ---------------------- 单元测试入口文件
        |- karma.conf.js  ----------------- karma配置文件
|- .babelrc  ------------------------------ babel 配置文件
|- .eslintignore  ------------------------- eslint规则例外配置目录
|- .eslintrc  ----------------------------- eslint规则配置目录
|- .gitignore  ---------------------------- git例外目录
|- .babelrc  ------------------------------ babel 配置文件
|- .babelrc  ------------------------------ babel 配置文件
|- index.html  ---------------------------- HTML 模板
|- package.json  -------------------------- npm 配置文件
```

## # 环境变量配置


### API代理配置

/confing/index.js

```js
'use strict'
// Template version: 1.2.8
// see http://vuejs-templates.github.io/webpack for documentation.

// const path = require('path')

// module.exports = {
//   dev: {

    // Paths
    // assetsSubDirectory: 'static',
    // assetsPublicPath: '/',
    proxyTable: {
      '/asae-saas': {
        target:"http://192.168.168.67:58080/",// 设置你调用的接口域名和端口号 别忘了加http
        changeOrigin: true,
      }
    },

//     // Various Dev Server settings
//     host: 'localhost', // can be overwritten by process.env.HOST
//     port: 8080, // can be overwritten by process.env.PORT, if port is in use, a free one will be determined
//     autoOpenBrowser: false,
//     errorOverlay: true,
//     notifyOnErrors: true,
//     poll: false, // https://webpack.js.org/configuration/dev-server/#devserver-watchoptions-

//     // Use Eslint Loader?
//     // If true, your code will be linted during bundling and
//     // linting errors and warnings will be shown in the console.
//     useEslint: true,
//     // If true, eslint errors and warnings will also be shown in the error overlay
//     // in the browser.
//     showEslintErrorsInOverlay: false,

//     /**
//      * Source Maps
//      */

//     // https://webpack.js.org/configuration/devtool/#development
//     devtool: 'cheap-module-eval-source-map',

//     // If you have problems debugging vue-files in devtools,
//     // set this to false - it *may* help
//     // https://vue-loader.vuejs.org/en/options.html#cachebusting
//     cacheBusting: true,

//     cssSourceMap: true,
//   },

//   build: {
//     // Template for index.html
//     index: path.resolve(__dirname, '../dist/index.html'),

//     // Paths
//     assetsRoot: path.resolve(__dirname, '../dist'),
//     assetsSubDirectory: 'static',
//     assetsPublicPath: '/',

//     /**
//      * Source Maps
//      */

//     productionSourceMap: true,
//     // https://webpack.js.org/configuration/devtool/#production
//     devtool: '#source-map',

//     // Gzip off by default as many popular static hosts such as
//     // Surge or Netlify already gzip all static assets for you.
//     // Before setting to `true`, make sure to:
//     // npm install --save-dev compression-webpack-plugin
//     productionGzip: false,
//     productionGzipExtensions: ['js', 'css'],

//     // Run the build command with an extra argument to
//     // View the bundle analyzer report after build finishes:
//     // `npm run build --report`
//     // Set to `true` or `false` to always turn it on or off
//     bundleAnalyzerReport: process.env.npm_config_report
//   }
}

```

### 路径别名设定

/build/webpack.base.conf.js

```js
'use strict'
// const path = require('path')
// const utils = require('./utils')
// const config = require('../config')
// const vueLoaderConfig = require('./vue-loader.conf')

// function resolve (dir) {
//   return path.join(__dirname, '..', dir)
// }

// const createLintingRule = () => ({
//   test: /\.(js|vue)$/,
//   loader: 'eslint-loader',
//   enforce: 'pre',
//   include: [resolve('src'), resolve('test')],
//   options: {
//     formatter: require('eslint-friendly-formatter'),
//     emitWarning: !config.dev.showEslintErrorsInOverlay
//   }
// })

// module.exports = {
//   context: path.resolve(__dirname, '../'),
//   entry: {
//     app: './src/main.js'
//   },
//   output: {
//     path: config.build.assetsRoot,
//     filename: '[name].js',
//     publicPath: process.env.NODE_ENV === 'production'
//       ? config.build.assetsPublicPath
//       : config.dev.assetsPublicPath
//   },
  resolve: {
    extensions: ['.js', '.vue', '.json'],
    alias: {
      'vue$': 'vue/dist/vue.esm.js',
      '@': resolve('src'),
    }
  },
//   module: {
//     rules: [
//       ...(config.dev.useEslint ? [createLintingRule()] : []),
//       {
//         test: /\.vue$/,
//         loader: 'vue-loader',
//         options: vueLoaderConfig
//       },
//       {
//         test: /\.js$/,
//         loader: 'babel-loader',
//         include: [resolve('src'), resolve('test'), resolve('node_modules/webpack-dev-server/client')]
//       },
//       {
//         test: /\.(png|jpe?g|gif|svg)(\?.*)?$/,
//         loader: 'url-loader',
//         options: {
//           limit: 10000,
//           name: utils.assetsPath('img/[name].[hash:7].[ext]')
//         }
//       },
//       {
//         test: /\.(mp4|webm|ogg|mp3|wav|flac|aac)(\?.*)?$/,
//         loader: 'url-loader',
//         options: {
//           limit: 10000,
//           name: utils.assetsPath('media/[name].[hash:7].[ext]')
//         }
//       },
//       {
//         test: /\.(woff2?|eot|ttf|otf)(\?.*)?$/,
//         loader: 'url-loader',
//         options: {
//           limit: 10000,
//           name: utils.assetsPath('fonts/[name].[hash:7].[ext]')
//         }
//       }
//     ]
//   },
//   node: {
//     // prevent webpack from injecting useless setImmediate polyfill because Vue
//     // source contains it (although only uses it if it's native).
//     setImmediate: false,
//     // prevent webpack from injecting mocks to Node native modules
//     // that does not make sense for the client
//     dgram: 'empty',
//     fs: 'empty',
//     net: 'empty',
//     tls: 'empty',
//     child_process: 'empty'
//   }
}

```


### 生产环境-环境变量配置

/confing/prod.env.js

```js
'use strict'
module.exports = {
  APP_NAME: '"金灯塔 - 商业版"', // APP名称
  NODE_ENV: '"production"', // 生产环境
  ROUTER_MODE: '"history"', // 路由模式
  BASE_URL: '""', // 基础URL
  BASE_API_URL: '"/asae-saas"', // API的基础URL
  BASE_IMAGE_URL: '', // 图片的基础URL
  AJAX_TIMEOUT: '30000', // ajax超时时间
  COMPONENT_THEME: '"default"' // UI 皮肤
}

```

### 开发环境-环境变量配置

/confing/dev.env.js

```js

'use strict'
const merge = require('webpack-merge')
const prodEnv = require('./prod.env')

module.exports = merge(prodEnv, {
  NODE_ENV: '"development"' // 开发环境
})

```

## # 安装依赖

推荐使用npm安装依赖

```bash
npm install
```

## # 启动

```bash
npm run dev
```

## # 单元测试

```bash
npm run test
```

## # 构建

```bash
npm run build
```