# 业务

--- 

业务层中的business设计是以模块为中心。

## 使用样例

```js
/*
 * @Author: chenyusheng
 * @Date: 2018-01-21 16:03:03
 * @Last Modified by: chenyusheng
 * @Last Modified time: 2018-01-21 22:01:15
 * 订单支付
 */
import OrderPayModel from '@/model/orderPay'
import CancleOrderPay from '@/model/cancleOrderPay'
import EventBus from '@/services/EventBus'
const orderPayModel = new OrderPayModel()
const cancleOrderPayModel = new CancleOrderPay()

const actions = {
  /**
   * 支付
   * @param {Object} param0
   * @param {Object} param1
   * @param {String} param1.order_id id
   */
  async salePaly ({commit}, {order_id}) {
    const {status} = await orderPayModel.set({order_id}).put()
    if (status === 'success') {
      EventBus.$emit('success', '支付成功！')
      return true
    }
    return false
  },
  /**
   * 取消支付
   * @param {Object} param0
   * @param {Object} param1
   * @param {String} param1.order_id id
   */
  async canclePlay ({commit}, {order_id}) {
    const {status} = await cancleOrderPayModel.set({order_id}).put()
    if (status === 'success') {
      EventBus.$emit('success', '取消成功！')
      return true
    }
    return false
  }
}

export default {
  actions
}


```

## 指导意见

- 接入vuex的业务文件全部以模块名称命名，并放入`src/business/`文件夹中，定义的业务文件必须在`src/business/index.js`中引用才可接入vuex;
- 业务modules中主要处理与model层对接的数据CRUD以及业务数据拼装工作。
- 统一的提示类消息，可在business层通过event-bus向view视图层抛出。
- 模块中需要共享的状态，应该交由business中的state管理，并由getters向其他模块共享。
- state的状态变化，统一由mutations处理。
- view尽量通过dispatch调用store。