
# 验证器

---

验证器主要是对自定义表单验证的统一管理，接入vuex store 以满足模块间验证共享。

`举个栗子`：

```js
export default {
  name: 'form',
  data () {
    let checkAge=(rules,value,callback)=>{
      this.$store.dispatch('checkAge',{rules,value,callback})
    }
    return {
      rules: {
        age: [{required: true, trigger: 'blur', validator: checkAge}]
      }
    }
  }
}
```

`/src/validate/index`

```js
const actions = {
  checkAge ({commit}, {rules,value,callback}) {
    if (value) {
      callback(new Error('年龄不能为空'))
    } else if (typeof value != 'number') {
      callback(new Error('年龄必须为数字'))
    } else {
      if (value > 65) {
        callback(new Error("年纪太大"))
      } else if (value < 18) {
        callback(new Error('年龄小了点，无法接受'))
      } else {
        callback()
      }
    }
  }
}

export default actions
```

> 表单验证语法糖

在vue组件中

> vm: 表单实例

```js
this.$validateForm(vm)
  .then(valid => {
    if (valid) {
      // success
    }
  })

```

在store中

> vm: 表单实例

```js
actions: {
  async loginSystem ({commit, dispatch}, vm) {
    const valid = await dispatch('validateForm', {vm})
    if (valid) {
      // success
    }
  }
}

```

表单验证失败时，系统会自动发出 “表单验证失败” 提示