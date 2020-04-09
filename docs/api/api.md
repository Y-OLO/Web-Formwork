# API接口定义

---

统一管理与后台对接的API

## 指导意见

- 所有与后台关联的url在/api/index.js文件定义
- 通过const定义常量
- 常量名称已`API_`开头，大写。

定义样例：

```js
export const API_MENUS = '/menus' // 系统menus
```

## 框架自带API

```js
export const API_LOGIN = '/login' // 登录
export const API_LOGOUT = '/logout' // 登出
```