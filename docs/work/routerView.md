# 化整为零
--- 

>如何切分页面？

## # 1、通过路由切割“页面级”粒度的功能模块

![](_media/页面切分路由样例.png)

## # 2、同一“页面”内的模块再划分

### 划分原则：

- `纵向`：通过业务功能（可根据视图模块判断）划分
- `横向`：通过Model-View-Controller三种不同职能划分

![](_media/页面模块切割.png)

![](_media/WX20180120-213518.png)

- 文件夹分级及组件划分
  - `SalesList.vue`: 主模块
  - `SalesOperate.vue`: 列表操作模块
  - `SalesPlay.vue`: 支付模块
  - `SalesSearch.vue`: 查询视图模块
  - `SalesTable.vue`: 订单列表模块

![](_media/salesList.png)

## # 3、合并同类项

继续细分粒度，然后将可复用模块或组件抽离到公共区域`"/src/views/components/"`

