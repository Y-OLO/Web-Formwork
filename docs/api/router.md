# 路由
---

## # 指导建议

- 路由以领域或模块为文件分类，以领域或模块为文件名，存放在`src/router/`文件夹下。
- 领域或模块定义的路由文件需要在`src/router/routes`文件中引入

## # 样例

src/router/order.js

```js
import Layout from '@/views/layout'
import RouterLayout from '@/components/layout/RouterLayout'
const _import = require('./_import_' + process.env.NODE_ENV)

const orderRoutes = [
  {
    path: '/order',
    component: Layout,
    redirect: '/order/sales',
    children: [
      {
        path: 'sales',
        name: 'sales',
        redirect: '/order/sales/index',
        component: RouterLayout,
        meta: { title: '销售订单表' },
        children: [
          {
            path: 'index',
            name: '/order/sales/index',
            component: _import('order/sales/SalesList'),
            meta: { title: '列表' }
          }
        ]
      }
    ]
  }
]
export default orderRoutes


```

src/router/routes.js

```js
import order from './order'
export default [
  ...order
]
```