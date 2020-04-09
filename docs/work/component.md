# 视图层组件

---

组件根据职责划分为两类

- 容器型组件
- 展示型组件

## # 容器型组件

容器型组件是与vuex store直连的组件，为展示型组件或其它容器组件提供数据和行为，尽量避免在其中做一些界面渲染相关的事情。


## # 展示型组件

展示型组件独立于应用的其它部分内容，不关心数据的加载和变更，保持职责单一，仅做视图呈现和最基本交互行为，通过props接收数据和回调函数输出结果，保证接收的数据为组件数据依赖的最小集。

>有图有真相

![](_media/WX20180120-230401.png)

容器型组件

`举个栗子`：

Home.vue

```html
<template>
  <div class="Home">
    <BaseRow class="Home_cards">
      <BaseCol span="6" v-for="item in items" :key="item.id">
        <BaseStaCard :BgColor="item.bgcolor" :IconType="item.icontype" :Title="item.title" :Num="item.num" :Unit="item.unit"></BaseStaCard>
      </BaseCol>
    </BaseRow>
  </div>
</template>

<script>
  import BaseStaCard from './BaseStaCard'
  export default {
    name: 'Home',
    data () {
      return {
        items: [
          {
            bgcolor: 'red',
            icontype: 'bar-chart-o',
            title: '今日销售',
            num: '0.00',
            unit: '元'
          },
          {
            bgcolor: 'blue',
            icontype: 'area-chart',
            title: '本月销售',
            num: '0.00',
            unit: '元'
          },
          {
            bgcolor: 'purple',
            icontype: 'group',
            title: '客户总数',
            num: '127',
            unit: '个'
          },
          {
            bgcolor: 'brown',
            icontype: 'cubes',
            title: '产品总数',
            num: '669',
            unit: '个'
          },
          {
            bgcolor: 'purple',
            icontype: 'line-chart',
            title: '日销售增长率',
            num: '0.00',
            unit: '%'
          },
          {
            bgcolor: 'brown',
            icontype: 'pie-chart',
            title: '月销售增长率',
            num: '0.00',
            unit: '%'
          },
          {
            bgcolor: 'red',
            icontype: 'user-plus',
            title: '客户增长率',
            num: '0.00',
            unit: '%'
          },
          {
            bgcolor: 'blue',
            icontype: 'dollar',
            title: '新产品销售额',
            num: '0.00',
            unit: '元'
          }
        ]
      }
    },
    components: {
      BaseStaCard
    }
  }
</script>
```

展示型组件

`举个栗子`：

BaseStaCard.vue

```html
<template>
  <BaseCard :class="BgColor" class="BaseStaCard">
    <BaseIcon :type="IconType" size="40"></BaseIcon>
    <h3>{{title}}</h3>
    <span>{{num}}<i>{{unit}}</i></span>
  </BaseCard>
</template>

<script>
export default {
  name: 'BaseStaCard',
  props: {
    bgColor: {
      type: String,
      required: true
    },
    iconType: {
      type: String,
      required: true
    },
    title: {
      type: String,
      required: true
    },
    num: {
      type: String,
      required: true
    },
    unit: {
      type: String
    }
  }
}
</script>
<style lang="less">
.BaseStaCard {
  font-size: 16px;
  position: relative;
  padding: 8px 16px;
  &.red {
    background: #fb7884;
  }
  &.blue {
    background: #03a9f3;
  }
  &.purple {
    background: #9675ce;
  }
  &.brown {
    background: #fca489;
  }
  .fa-icon {
    color: #fff;
    position: absolute;
    left: 24px;
    top: 32px;
  }
  h3 {
    color: #fff;
    text-align: right;
    font-size: 16px;
    font-weight: 400;
    padding-top: 0;
    margin-top: 8px;
    margin-bottom: 8px;
  }
  span {
    text-align: right;
    display: block;
    clear: both;
    font-size: 24px;
    i {
      font-size: 14px;
      margin-left: 5px;
      font-style: normal;
    }
  }
}
</style>

```