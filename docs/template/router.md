# 路由模板

---

```js
import Layout from '@/views/layout'
import RouterLayout from '@/components/layout/RouterLayout'
const _import = require('./_import_' + process.env.NODE_ENV)
const `模块名称`Routes = [
  {
    path: '/一级路径',
    component: Layout,
    redirect: '/一级路径/二级路径',
    children: [
      {
        path: '二级路径',
        name: '/一级路径/二级路径',
        redirect: '/一级路径/二级路径/三级路径',
        component: RouterLayout,
        meta: { title: '名称' },
        children: [
          {
            path: '三级路径',
            name: '/一级路径/二级路径/三级路径',
            component:  _import('组件路径不含views/'),
            meta: { title: '名称' }
          }
        ]
      }
    ]
  }
]
export default `模块名称`Routes
```