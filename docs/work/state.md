# 应用状态模型
---

>我勒个去，这又是什么鬼？和之前说的领域模型有啥区别？

应用状态模型是与视图相关的状态数据。

`举个栗子`：

- 当前页面选中了列表的第n行 currentSelectedRow: someId
- 模态框是否弹出
- 列表所展现的数据

> 列表所展现的数据？ 这不是领域模型中的数据么？

实际上领域模型与视图并没有`直接`关系,领域模型中的数据通过应用状态模型`加工`后提供给视图层。