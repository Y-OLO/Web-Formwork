# BaseTable 表格组件
---

## # 功能
>基础表格， 集合了iview的table组件以及page组件。

## # 效果图
![](_media/BaseTable.png)

## # 使用

- data类型为 Array 的使用方式

```html
<template>
  <BaseTable :columns="columns1" :data="data"></BaseTable> 
</template>

<script>
export default {
  data () {
    return {
      height: 300,
      columns1: [
        {
          title: 'Name',
          key: 'name',
          width: 100
        },
        {
          title: 'Age',
          key: 'age'
        },
        {
          title: 'Address',
          key: 'address'
        }
      ],
      data: [
        {
          name: 'John Brown',
          age: 18,
          address: 'New York No. 1 Lake Park',
          date: '2016-10-03'
        },
        {
          name: 'Jim Green',
          age: 24,
          address: 'London No. 1 Lake Park',
          date: '2016-10-01'
        },
        {
          name: 'Joe Black',
          age: 30,
          address: 'Sydney No. 1 Lake Park',
          date: '2016-10-02'
        }
      ]
    }
  }
}
</script>
```

- data类型为 数据模型 的使用方式

```htm
<template>
  <BaseTable height="auto" :data="data"  :columns="columns" vm="salsTable" />  
</template>

<script>
import ButtonSalesPlay from './ButtonSalesPlay'
import DropdownSalesOperate from './DropdownSalesOperate'
export default {
  name: 'TableSales',
  components: {
    ButtonSalesPlay,
    DropdownSalesOperate
  },
  data () {
    return {
      data: this.$store.state.sales.salesModel,
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
              <ButtonSalesPlay order-id={orderId} is-pay={isPay} status={status}/>
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
            return (
              <DropdownSalesOperate />
            )
          }
        }
      ]
    }
  }
}
</script>
```

扩展位填充

```html
<template>
  <BaseTable :columns="columns1" :data="fetchData">
  </BaseTable> 
</template>
<template>
  <BaseTable height="auto" :data="data"  :columns="columns" vm="salsTable" >
    <div slot="extend">扩展位</div>    
  </BaseTable>  
</template>

<script>
import ButtonSalesPlay from './ButtonSalesPlay'
import DropdownSalesOperate from './DropdownSalesOperate'
export default {
  name: 'TableSales',
  components: {
    ButtonSalesPlay,
    DropdownSalesOperate
  },
  data () {
    return {
      data: this.$store.state.sales.salesModel,
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
              <ButtonSalesPlay order-id={orderId} is-pay={isPay} status={status}/>
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
            return (
              <DropdownSalesOperate />
            )
          }
        }
      ]
    }
  }
}
</script>
```

## # API

此组件继承iview [Table组件的API](https://www.iviewui.com/components/Table)内容

新增API

BaseTable props

参数 | 说明 | 类型 | 可选值 | 默认值
--- |---   |---  |---    |--- 
data | 列表数据 | [Array, Function]  | — | []
showTotal | 是否显示数据总数 | Boolean | — | true
showIndex | 是否显示行号 | Boolean | — | true
showSelection | 是否多选selection | Boolean | — | false
hasPaging | 是否分页 | Boolean | — | true
pageSize | 每页显示数量 | Number | — | 25



