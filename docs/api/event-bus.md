# 事件总线
---

## # 成功消息

```js
import EventBus from '@/services/EventBus'
EventBus.$emit('success', '执行成功')
```

## # 失败消息

```js
import EventBus from '@/services/EventBus'
EventBus.$emit('error', '执行失败')
```

## # 提醒消息

```js
import EventBus from '@/services/EventBus'
EventBus.$emit('info', '您所在地为：大连')
```

## # 警告消息

```js
import EventBus from '@/services/EventBus'
EventBus.$emit('warning', '账号登录异常')
```
