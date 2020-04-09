# Duplicate declaration "h" (This is an error on an internal node. Probably an internal error)

> 修改babel配置

.babelrc

```js
{
  "presets": [
    ["env", {
      "modules": false,
      "targets": {
        "browsers": ["> 1%", "last 2 versions", "not ie <= 8"]
      }
    }],
    "stage-2"
  ],
  "plugins": ["transform-vue-jsx", "transform-runtime"],
  "env": {
    "test": {
      "presets": ["env", "stage-2"],
      // "plugins": ["transform-vue-jsx", "istanbul"] // 数组中删除 transform-vue-jsx
      "plugins": ["istanbul"] // 删除后
    }
  }
}

```