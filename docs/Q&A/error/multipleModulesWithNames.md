# There are multiple modules with names that only differ in casing.

> 完整错误信息

```
There are multiple modules with names that only differ in casing.
This can lead to unexpected behavior when compiling on a filesystem with other case-semantic
```

> 原因

- 组件中存在多个name相同的组件
- 引用组件时候，路径的大小写错误

`举个栗子`:

错误：

```js
require(['../views/order/sales/Saleslist.vue']
```

正确：

```js
require(['../views/order/sales/SalesList.vue']
```

