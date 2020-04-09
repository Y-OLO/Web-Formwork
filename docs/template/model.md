# Model | Collection模板

## Model 模板

```js
import {Model} from '@/services/Schema'
import {API_`改我`} from '@/api'

const `模型名称` = Model.extend({
  // url: '', // 后台API URL
  // defaults: {}, // 默认值
  // parse: (data) => data, // set时触发
  // methods: {}, // 扩展方法
})

export default `模型名称`
```

## Collection 模板

```js
import {Collection} from '@/services/Schema'
import {API_`改我`} from '@/api'

const `集合名称` = Collection.extend({
  // url: '', // 后台API URL
  // defaults: [] // 默认值
  // parse: (data) => data, // fetch时触发
  // cache: 'noCache', // 缓存策略: 默认 = `'noCache'`：不缓存； = `'session'`：随浏览器session缓存，浏览器关闭后清除缓存； = `'local'`：
  // model: , // 模型继承
})

export default `集合名称`

```