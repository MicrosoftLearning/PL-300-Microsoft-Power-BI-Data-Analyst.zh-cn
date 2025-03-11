---
demo:
  title: 在 Power BI 中使用 DAX 创建度量值
  module: Create measures using DAX in Power BI
---
# 在 Power BI 中使用 DAX 创建度量值

> **提示**：可以从 D:\Allfiles\Demo\Resources\Snippets-Demo-05.txt 文件复制所有计算。

## 创建计算表

1. 使用以下表达式创建一个计算表：

```dax
Date = CALENDARAUTO()
```

1. 切换到“数据”视图，然后查看包含一个“日期”列的表。

创建计算列

1. 在“日期”表中添加一个计算列：

```dax
Year = "CY" & YEAR('Date'[Date])
```

1. 在“日期”表中添加一个附加的计算列：

```dax
Month = FORMAT('Date'[Date], "YYYY-MM")
```

1. 在“模型”视图中，通过将“日期”表中的“日期”列拖到“销售额”表中的“OrderDate”列来创建关系。

1. 隐藏“销售额”表中的 OrderDate 列。

1. 在“日期”表中，创建具有“年份”和“月份”级别的“日历”层次结构。

1. 在“报表”视图中，使用“日期”列将“日期”表标记为日期表。

1. 在矩阵视觉对象中，删除“产品”层次结构，然后将其替换为“日历”层次结构。

1. 在“销售额”表中添加一个计算列：

```dax
Cost = 'Sales'[Quantity] * RELATED('Product'[Cost])
```

1. 将“成本”列的格式设置为两位小数。

## 创建快速度量

1. 将快速度量添加到“销售业绩”表中，然后从“销售业绩”列中去掉“成本”列。

1. 将度量值重命名为“利润”。

1. 说明该度量值未在模型中存储数据。

创建常规度量值

1. 在“销售额”表中添加一个度量值：

```dax
Profit Margin = DIVIDE([Profit], SUM('Sales'[Sales]))
```

1. 将“利润率”列的格式设置为百分比。

1. 在“销售额”表中添加另一个度量值：

```dax
Sales YTD = TOTALYTD(SUM('Sales'[Sales]), 'Date'[Date])
```

1. 将“年初至今销售额”列的格式设置为两位小数。

## 使用矩阵视觉对象验证计算

1. 将“成本”、“利润”、“利润率”和“年初至今销售额”字段添加到矩阵视觉对象中。

1. 保存 Power BI Desktop 文件。

1. 让 Power BI Desktop 文件保持打开状态，以便在后续演示中使用该文件。
