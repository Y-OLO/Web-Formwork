# 业务modules 模板

---

```js
import {`在mutation-types.js中定义的名称`} = '@/business/mutation-types'

import `模型或集合**首字母大写**`Model from '@/model/`模型或集合`'

const `模型或集合**首字母小写**` = new `模型或集合**首字母大写**`()

const state = function () {
  return {}
}

const getters = {
  `名称` (state) {
    return stata.`返回值`
  }
}

const mutations = {
  [`在mutation-types.js中定义的名称`] (state, payload) {

  }
}

const actions = {
  `名称` ({state, rootState, commit, dispatch, getters, rootGetters}, params) {
    
  }
}

export default {
  state,
  getters,
  mutations,
  actions
}
```