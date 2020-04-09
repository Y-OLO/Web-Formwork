# vue单元测试：PhantomJS 2.1.1 ERROR: Can't find variable: Promise

> PhantomJS 2.1.1 并不支持 Promise，需要使用 "promise-polyfill"

安装

```bash
$ npm install promise-polyfill --save-exact
```

test/unit/index.js

```js
import 'promise-polyfill/src/polyfill'
```