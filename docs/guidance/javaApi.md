# 与后台API对接规范指南
---

> RESTful API

## # HTTP动词

- GET（SELECT）：从服务器取出资源（一项或多项）。
- POST（CREATE）：在服务器新建一个资源。
- PUT（UPDATE）：在服务器更新资源（客户端提供改变后的完整资源）。
- PATCH（UPDATE）：在服务器更新资源（资源局部修改）。
- DELETE（DELETE）：从服务器删除资源。
- HEAD：获取资源的元数据。

`举个栗子`：

- GET /zoos：列出所有动物园
- POST /zoos：新建一个动物园
- GET /zoos/ID：获取某个指定动物园的信息
- PUT /zoos/ID：更新某个指定动物园的信息（提供该动物园的全部信息）
- PATCH /zoos/ID：更新某个指定动物园的信息（提供该动物园的部分信息）
- DELETE /zoos/ID：删除某个动物园
- GET /zoos/ID/animals：列出某个指定动物园的所有动物
- DELETE /zoos/ID/animals/ID：删除某个指定动物园的指定动物

## # response

> 类型：Object

```js
{
  code, // code状态码
  flg, // flg标识
  msg, // 消息
  data: // 数据
}
```

## # 状态码

>优先级： flg > code

### flg

- 1 : 成功
- 0 : 失败


### code

- code >= 100000 && code < 200000 : 成功
- code < 100000 || code >= 200000 : 失败

## # 消息

请求所返回的错误消息通过msg返回