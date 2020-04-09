## 工具集合

---

## Constants

<dl>
<dt><a href="#inBrowser">inBrowser</a></dt>
<dd><p>判断是否为浏览器环境</p>
</dd>
<dt><a href="#isIE">isIE</a></dt>
<dd><p>判断是否为IE</p>
</dd>
<dt><a href="#isIE9">isIE9</a></dt>
<dd><p>判断是否为IE9</p>
</dd>
<dt><a href="#isEdge">isEdge</a></dt>
<dd><p>判断是否为Edge</p>
</dd>
<dt><a href="#isAndroid">isAndroid</a></dt>
<dd><p>判断是否为Android</p>
</dd>
<dt><a href="#isIOS">isIOS</a></dt>
<dd><p>判断是否为Ios</p>
</dd>
<dt><a href="#isChrome">isChrome</a></dt>
<dd><p>判断是否为Chrome</p>
</dd>
</dl>

## Functions

<dl>
<dt><a href="#findComponentUpward">findComponentUpward(context, componentName, componentNames)</a> ⇒</dt>
<dd><p>查找父组件</p>
</dd>
<dt><a href="#findComponentDownward">findComponentDownward(context, componentName)</a> ⇒</dt>
<dd><p>查找第一个符合条件的子组件</p>
</dd>
<dt><a href="#findComponentsDownward">findComponentsDownward(context, componentName)</a> ⇒</dt>
<dd><p>查找所有满足条件的子组件</p>
</dd>
<dt><a href="#oneOf">oneOf(value, validList)</a> ⇒</dt>
<dd><p>判断参数是否是其中之一</p>
</dd>
<dt><a href="#isFunction">isFunction(valid)</a> ⇒</dt>
<dd><p>判断参数的类型是否为function</p>
</dd>
<dt><a href="#isString">isString(param)</a> ⇒ <code>Boolean</code></dt>
<dd><p>是否为字符串验证</p>
</dd>
<dt><a href="#isNumber">isNumber(param)</a> ⇒ <code>Boolean</code></dt>
<dd><p>是否为数字验证</p>
</dd>
<dt><a href="#isUndefined">isUndefined(param)</a> ⇒ <code>Boolean</code></dt>
<dd><p>是否为undefined验证</p>
</dd>
<dt><a href="#isArray">isArray(param)</a> ⇒ <code>Boolean</code></dt>
<dd><p>是否为数组验证</p>
</dd>
<dt><a href="#isObject">isObject(param)</a> ⇒ <code>Boolean</code></dt>
<dd><p>是否为对象验证</p>
</dd>
<dt><a href="#deepClone">deepClone(obj)</a> ⇒</dt>
<dd><p>深度克隆</p>
</dd>
<dt><a href="#compilePath">compilePath(path, params)</a> ⇒</dt>
<dd><p>path路径补全</p>
</dd>
<dt><a href="#firstLetterToUpperCase">firstLetterToUpperCase(str)</a> ⇒</dt>
<dd><p>首字符大写</p>
</dd>
</dl>

<a name="inBrowser"></a>

## inBrowser
判断是否为浏览器环境

**Kind**: global constant  
**Example**  
```js
import {inBrowser} from '@/utils/env'
if (inBrowser) {
  // coding...
}
```
<a name="isIE"></a>

## isIE
判断是否为IE

**Kind**: global constant  
**Example**  
```js
import {isIE} from '@/utils/env'
if (isIE) {
  // coding...
}
```
<a name="isIE9"></a>

## isIE9
判断是否为IE9

**Kind**: global constant  
**Example**  
```js
import {isIE9} from '@/utils/env'
if (isIE9) {
  // coding...
}
```
<a name="isEdge"></a>

## isEdge
判断是否为Edge

**Kind**: global constant  
**Example**  
```js
import {isEdge} from '@/utils/env'
if (isEdge) {
  // coding...
}
```
<a name="isAndroid"></a>

## isAndroid
判断是否为Android

**Kind**: global constant  
**Example**  
```js
import {isAndroid} from '@/utils/env'
if (isAndroid) {
  // coding...
}
```
<a name="isIOS"></a>

## isIOS
判断是否为Ios

**Kind**: global constant  
**Example**  
```js
import {isIOS} from '@/utils/env'
if (isIOS) {
  // coding...
}
```
<a name="isChrome"></a>

## isChrome
判断是否为Chrome

**Kind**: global constant  
**Example**  
```js
import {isChrome} from '@/utils/env'
if (isChrome) {
  // coding...
}
```
<a name="findComponentUpward"></a>

## findComponentUpward(context, componentName, componentNames) ⇒
查找父组件

**Kind**: global function  
**Returns**: 查找到的父组件  
**Export**:   

| Param | Type | Description |
| --- | --- | --- |
| context | <code>any</code> | 上下文 |
| componentName | <code>any</code> | 查找父组件名称 |
| componentNames | <code>any</code> | 查找父组件名称集合 |

<a name="findComponentDownward"></a>

## findComponentDownward(context, componentName) ⇒
查找第一个符合条件的子组件

**Kind**: global function  
**Returns**: 第一个符合条件的子组件  
**Export**:   

| Param | Type | Description |
| --- | --- | --- |
| context | <code>any</code> | 上下文 |
| componentName | <code>any</code> | 查找的子组件名称 |

<a name="findComponentsDownward"></a>

## findComponentsDownward(context, componentName) ⇒
查找所有满足条件的子组件

**Kind**: global function  
**Returns**: 所有满足条件的子组件  
**Export**:   

| Param | Type | Description |
| --- | --- | --- |
| context | <code>any</code> | 上下文 |
| componentName | <code>any</code> | 查找的子组件名称 |

<a name="oneOf"></a>

## oneOf(value, validList) ⇒
判断参数是否是其中之一

**Kind**: global function  
**Returns**: true or false  

| Param | Type | Description |
| --- | --- | --- |
| value | <code>String</code> | 值 |
| validList | <code>Array</code> | 数组 |

**Example**  
```js
import {oneOf} from @/utils/assist
// return true
oneOf('no', ['yes', 'no'])
// return false
oneOf('hello', ['yes', 'no'])
```
<a name="isFunction"></a>

## isFunction(valid) ⇒
判断参数的类型是否为function

**Kind**: global function  
**Returns**: true or false  

| Param | Type | Description |
| --- | --- | --- |
| valid | <code>\*</code> | 参数 |

**Example**  
```js
import {isFunction} from @/utils/assist
// return true
const funs = function () {}
isFunction(funs)
// return false
const str = 'str111'
isFunction(str)
```
<a name="isString"></a>

## isString(param) ⇒ <code>Boolean</code>
是否为字符串验证

**Kind**: global function  

| Param | Type | Description |
| --- | --- | --- |
| param | <code>\*</code> | 需验证的参数 |

**Example**  
```js
import {isString} from @/utils/assist
// return true
isString('cys')
// return false
isString({name: 'cys'})
```
<a name="isNumber"></a>

## isNumber(param) ⇒ <code>Boolean</code>
是否为数字验证

**Kind**: global function  

| Param | Type | Description |
| --- | --- | --- |
| param | <code>\*</code> | 需验证的参数 |

**Example**  
```js
import {isNumber} from @/utils/assist
// return true
isNumber(111)
// return false
isNumber('cys')
```
<a name="isUndefined"></a>

## isUndefined(param) ⇒ <code>Boolean</code>
是否为undefined验证

**Kind**: global function  

| Param | Type | Description |
| --- | --- | --- |
| param | <code>\*</code> | 需验证的参数 |

**Example**  
```js
import {isUndefined} from @/utils/assist
// return true
isUndefined(undefined)
// return false
isUndefined({name: 'cys'})
```
<a name="isArray"></a>

## isArray(param) ⇒ <code>Boolean</code>
是否为数组验证

**Kind**: global function  

| Param | Type | Description |
| --- | --- | --- |
| param | <code>\*</code> | 需验证的参数 |

**Example**  
```js
import {isArray} from @/utils/assist
// return true
isArray(['cys'])
// return false
isArray({name: 'cys'})
```
<a name="isObject"></a>

## isObject(param) ⇒ <code>Boolean</code>
是否为对象验证

**Kind**: global function  

| Param | Type | Description |
| --- | --- | --- |
| param | <code>\*</code> | 需验证的参数 |

**Example**  
```js
import {isObject} from @/utils/assist
// return true
isObject({name: 'cys'})
// return false
isObject(['cys'])
```
<a name="deepClone"></a>

## deepClone(obj) ⇒
深度克隆

**Kind**: global function  
**Returns**: 新的对象  

| Param | Type | Description |
| --- | --- | --- |
| obj | <code>\*</code> | 需要clone的对象 |

**Example**  
```js
import {deepClone} from @/utils/assist
const newObject = deepClone(superObject)
```
<a name="compilePath"></a>

## compilePath(path, params) ⇒
path路径补全

**Kind**: global function  
**Returns**: 完整path  

| Param | Type | Description |
| --- | --- | --- |
| path | <code>String</code> | 补全路径 |
| params | <code>Object</code> | 参数 |

**Example**  
```js
import {compilePath} from @/utils/assist
//  return '/user/123'
compilePath('/user/:id', { id: 123 })
```
<a name="firstLetterToUpperCase"></a>

## firstLetterToUpperCase(str) ⇒
首字符大写

**Kind**: global function  
**Returns**: 转换后的字符串  

| Param | Type | Description |
| --- | --- | --- |
| str | <code>Sring</code> | 需要转换的字符串 |

**Example**  
```js
import {firstLetterToUpperCase} from @/utils/assist
// return 'Cys'
firstLetterToUpperCase('cys')
```
