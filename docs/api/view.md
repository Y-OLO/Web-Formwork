# 视图

---

- 以vue单文件组件方式定义 `.vue`
- 视图以业务模块进行分类，根据模块的复杂程度可分2级或3级
- 单vue视图代码量100行以内为最佳，超过200行代码会导致难以维护，建议复杂视图拆分成子视图或功能组件


## # 视图及业务组件拆分样例

- 最终

![](_media/salesTable.png)

- 文件夹分级及组件划分
  - `SalesList.vue`: 主模块
  - `SalesOperate.vue`: 列表操作模块
  - `SalesPlay.vue`: 支付模块
  - `SalesSearch.vue`: 查询视图模块
  - `SalesTable.vue`: 订单业务列表模块

![](_media/salesList.png)


SalesList.vue

```html
<template>
  <TableLayout >
    <SalesSearch slot="searchbar" />
    <SalesTable slot="table" />
  </TableLayout>
</template>

<script>
import SalesSearch from './SalesSearch'
import SalesTable from './SalesTable'
import TableLayout from '@/components/layout/TableLayout'
export default {
  name: 'SalesList',
  components: {
    SalesSearch,
    SalesTable,
    TableLayout
  }
}
</script>
```

SalesOperate.vue

```html
<template>
  <BaseTableOperatingButtons :buttons="buttons"></BaseTableOperatingButtons>
</template>

<script>
export default {
  name: 'SalesOperate',
  data () {
    return {
      buttons: [
        {
          name: '删除',
          icon: 'home',
          click: (item, index) => {
            // 删除逻辑
          }
        }
      ]
    }
  }
}
</script>
```


SalesPlay.vue

```html
<template>
  <div>
    {{text}}
    <BaseButton v-if="!saleIsPay" style="color:red;" type="text" icon="checkmark" shape="circle" size="small"  @click="handlePlay"></BaseButton>
    <BaseButton v-if="saleIsPay && saleStatus === 'RUN'" style="color:red;" type="text" icon="close" shape="circle" size="small"  @click="handleCancelplay"></BaseButton>
  </div>
</template>

<script>
export default {
  name: 'SalesPlay',
  data () {
    return {
      saleIsPay: this.isPay,
      saleStatus: this.status
    }
  },
  props: {
    orderId: {
      type: String,
      required: true
    },
    isPay: {
      type: Number,
      required: true
    },
    status: {
      type: String,
      required: true
    }
  },
  computed: {
    text () {
      return this.saleIsPay === 0 ? '未结款' : this.saleIsPay === 1 ? '已结款' : ''
    }
  },
  methods: {
    handlePlay () {
      this.$Modal.confirm({
        title: '支付',
        content: '确认支付？',
        loading: true,
        okText: '支付',
        onOk: async () => {
          const result = await this.$store.dispatch('sales/salePaly', {order_id: this.orderId})
          if (result) this.saleIsPay = 1
          this.$Modal.remove()
        }
      })
    },
    handleCancelplay () {
      this.$Modal.confirm({
        title: '取消支付',
        content: '确认取消支付？',
        loading: true,
        okText: '确认取消支付',
        onOk: async () => {
          const result = await this.$store.dispatch('sales/canclePlay', {order_id: this.orderId})
          if (result) this.saleIsPay = 0
          this.$Modal.remove()
        }
      })
    }
  }
}
</script>


```

SalesTable.vue

```html
<template>
  <Form inline>
    <FormItem prop="mistiness">
      <BaseInputSearch placeholder="订单号/客户名称"></BaseInputSearch>
    </FormItem>
    <FormItem>
      <BaseDatePicker type="daterange" placement="bottom-start" placeholder="请选择起始时间" style="width: 215px"></BaseDatePicker>
    </FormItem>
    <FormItem>
      <BaseButtonSearch @click="search"></BaseButtonSearch>
    </FormItem>
    <FormItem class="AppButtonRightTop">
      <BaseButtonAdd @click="add"></BaseButtonAdd>
    </FormItem>
  </Form>
</template>

<script>
export default {
  name: 'SalesSearch',
  methods: {
    search () {
    },
    add () {
    }
  }
}
</script>

<style>
.AppButtonRightTop {
  float: right;
}
</style>

```

DropdownSalesOperate.vue

```html
<template>
  <BaseTable
    height="auto"
    :data="salesModel"
    :columns="columns"
    vm="salsTable" 
  />
</template>

<script>
import SalesPlay from './SalesPlay'
import SalesOperate from './SalesOperate'
import { mapState } from 'vuex'
export default {
  name: 'TableSales',
  components: {
    SalesPlay,
    SalesOperate
  },
  data () {
    return {
      columns: [
        {
          title: '订单号',
          width: 150,
          key: 'order_id'
        },
        {
          title: '客户名称',
          key: 'customer_name',
          width: 161,
          className: 'table-clamp-2'
        },
        {
          title: '金额',
          key: 'totalprice',
          align: 'right'
        },
        {
          title: '支付方式',
          width: 100,
          key: 'paymenttype',
          render: (h, params) => {
            const {row: {paymenttype}} = params
            return this.$t(`ORD_SALE_PAYMENTTYPE.${paymenttype}`)
          }
        },
        {
          title: '出库仓',
          key: 'depot_name'
        },
        {
          title: '状态',
          key: 'status',
          render: (h, params) => {
            const {status} = params.row
            return this.$t(`ORD_SALE_STATUS.${status}`)
          }
        },
        {
          title: '下单方式',
          key: 'tradefrom',
          width: 100
        },
        {
          title: '下单时间',
          key: 'create_time'
        },
        {
          title: '付款状态',
          width: 100,
          key: 'is_pay',
          render: (h, params) => {
            const {order_id: orderId, is_pay: isPay, status} = params.row
            return (
              <SalesPlay order-id={orderId} is-pay={isPay} status={status}/>
            )
          }
        },
        {
          title: '占用库存',
          width: 80,
          key: 'occupy_enable'
        },
        {
          title: '操作',
          key: 'action',
          search: false,
          align: 'right',
          width: 90,
          render: (h, params) => {
            // const {order_id: orderId, is_pay: isPay, status} = params.row
            return (
              <SalesOperate />
            )
          }
        }
      ]
    }
  },
  computed: {
    ...mapState({
      salesModel: state => state.salesTable.salesModel
    })
  }
}
</script>

```

