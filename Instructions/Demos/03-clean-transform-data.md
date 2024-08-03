---
demo:
  title: 在 Power BI 中清理、转换和加载数据
  module: 'Clean, transform, and load data in Power BI'
---

# 在 Power BI 中清理、转换和加载数据

## 应用查询转换

1. 首先，将转换应用于“产品”查询。

1. 删除“RetailPrice”、“照片”和“销售额”列。

1. 将“Channels”列的数据类型更改为“整数”。。

1. 为以下列重命名：

    - 将“ProductSKU”重命名为“SKU”

    - 将“ProductName”重命名为“Product” 

    - 将“ProductCategory”重命名为“类别”

    - 将“ItemGroup”重命名为“项目组”

    - 将“KitType”重命名为“套件类型”

1. 然后，将转换应用于“销售额”查询。

1. 删除所有列，以下列除外：

    - OrderDate

    - ProductID

    - 数量

    - 单价

1. 将 UnitPrice 列的数据类型更改为固定的十进制数。

1. 将“UnitPrice”列重命名为“单价”。

1. 同时选择“数量”和“单价”列，然后根据它们的乘积添加一个新列。

1. 将新列重命名为“销售额”。

## 整合查询

1. 使用 Excel 连接器创建一个新查询，连接到 D:\Allfiles\Demo\Data\ProductCost.xlsx 文件。

1. 删除“产品”列。

1. 将 ProductCost 列的数据类型更改为固定的十进制数。

1. 选择“产品”查询，然后将其与 ProductCost 查询合并，并与 SKU 列关联。

1. 在“隐私级别”窗口中，将 D:\ 的隐私级别设置为“组织”。

1. 展开 ProductCost 列以包括 ProductCost 列（来自 ProductCost 查询）。

1. 将新列重命名为“成本”。

## 禁用查询并将其加载到数据模型

1. 在“查询”窗格中，禁用 ProductCost 查询。

1. 在“主页”功能区选项卡上，单击“关闭并应用”图标。

1. 在 Power BI Desktop 中，指出“数据”窗格中的两个表。

1. 保存 Power BI Desktop 文件。

1. 让 Power BI Desktop 文件保持打开状态，以便在下一个演示中使用该文件。
