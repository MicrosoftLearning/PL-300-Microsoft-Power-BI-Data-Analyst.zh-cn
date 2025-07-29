---
lab:
  title: 在 Power BI 中使用 DAX 时间智能函数
  module: Use DAX time intelligence functions in Power BI
---

# 在 Power BI 中使用 DAX 时间智能函数

## 实验室场景

在本实验室中，你将使用涉及时间智能的 DAX 表达式创建度量值。

在本实验室中，了解如何：

 - 使用各种时间智能函数来操作特定关注日期的筛选器上下文。

此实验室应该大约需要 15 分钟。****

## 开始使用

若要完成本练习，请先打开 Web 浏览器并输入以下 URL 以下载 zip 文件：

`https://github.com/MicrosoftLearning/PL-300-Microsoft-Power-BI-Data-Analyst/raw/Main/Allfiles/Labs/06-use-dax-time-intelligence/06-time-intelligence.zip`

将文件解压缩到 C:\Users\Student\Downloads\06-time-intelligence 文件夹****。

打开 06-Starter-Sales Analysis.pbix**** 文件。

> _注意****：可以通过选择“取消”来取消登录****。关闭所有其他信息窗口。如果系统提示应用更改，请选择“稍后应用”****。_

## 创建 YTD 度量值

在此任务中，你将使用时间智能函数创建一个年初至今 (YTD) 的销售额度量值。

1. 在 Power BI Desktop 的“报表”视图中的“第 2 页”上，注意矩阵视觉对象显示了多个度量值，并在行上对年份和月份进行了分组****。

2. 根据以下表达式，向 `Sales` 表添加一个度量值，并将格式设置为没有小数位：

    ```dax
    Sales YTD =
    TOTALYTD(
        SUM(Sales[Sales]),
        'Date'[Date],
        "6-30"
    )
    ```

    > `TOTALYTD` 函数对给定日期列计算表达式（在本例中为对 `Sales` 列求和）。__ 日期列必须属于标记为日期表的 Date 表。
    >
    > 此函数还可以接受第三个可选参数，即表示一年中的最后一天。_如果没有此日期，则表示 12 月 31 日是一年中的最后一天。对于 Adventure Works，6 月是一年中的最后一个月，因此使用的是“6-30”。_

3. 将 `Sales` 字段和 `Sales YTD` 度量值添加到矩阵视觉对象。

4. 注意一年内销售额的累计。

    ![图 1](Linked_image_Files/06-use-dax-time-intelligence-functions_image21.png)

> _`TOTALYTD` 函数执行筛选器控制，特别是时间筛选器控制。例如，若要计算 2017 年 9 月（会计年度的第三个月）的 YTD 销售额，则会移除 `Date` 表上的所有筛选器，取而代之的是新筛选器，此筛选器筛选出从年初（2017 年 7 月 1 日）一直到上下文内日期期限的最后一天（2017 年 9 月 30 日）的所有日期。_
>
> DAX 中提供了许多[时间智能函数](/dax/time-intelligence-functions-dax/?azure-portal=true)来支持常见的时间筛选器控制。__

## 创建 YoY 增长率度量值

在此任务中，你将使用变量创建一个销售额同比增长的度量值。

> 变量有助于简化公式，如果在公式中多次使用逻辑，使用变量会更高效。 变量使用唯一名称进行声明，而度量值表达式必须在 `RETURN` 关键字之后输出。 与其他一些编码语言变量不同，DAX 变量只能在单个公式中使用。_

1. 基于以下表达式向 `Sales` 表添加其他度量值：

    ```dax
    Sales YoY Growth =
    VAR SalesPriorYear =
        CALCULATE(
            SUM(Sales[Sales]),
            PARALLELPERIOD(
                'Date'[Date],
                -12,
                MONTH
            )
        )
    RETURN
        SalesPriorYear
    ```

    > _为 `SalesPriorYear` 变量分配了一个表达式，该表达式可计算修改后的上下文中 `Sales` 列的总和。该上下文使用 `PARALLELPERIOD` 函数从筛选器上下文中的每个日期往回移 12 个月。_

1. 将 `Sales YoY Growth` 度量值添加到矩阵视觉对象。

1. 请注意，新的度量值对前 12 个月返回 `BLANK`（2017 会计年度之前没有任何销售额记录）。

1. 请注意，2018 年 7 月的 `Sales YoY Growth` 度量值的值是 2017 年 7 月的 Sales 值____。

    ![图 2](Linked_image_Files/06-use-dax-time-intelligence-functions_image22.png)

    > 至此，公式的“困难部分”已经过测试，可以用计算增长率结果的最终公式来覆盖此度量值了。__

1. 若要完成此度量值，请使用以下公式来覆盖 `Sales YoY Growth` 度量值，并将格式设置为有两位小数的百分比：

    ```dax
    Sales YoY Growth =
    VAR SalesPriorYear =
        CALCULATE(
            SUM(Sales[Sales]),
            PARALLELPERIOD(
                'Date'[Date],
                -12,
                MONTH
            )
        )
    RETURN
        DIVIDE(
            (SUM(Sales[Sales]) - SalesPriorYear),
            SalesPriorYear
        )
    ```

1. 在公式的 `RETURN` 子句中，我们注意到，变量被引用了两次。

1. 验证 2018 年 7 月的 YoY 增长率是否为 392.83%__。

    ![图片 3](Linked_image_Files/06-use-dax-time-intelligence-functions_image23.png)

    > YoY Growth 度量值表明，销售额比去年同期增长了近 400%（或 4 倍）。__

1. 在“模型”视图中，将这两个新度量值放入名为“Time intelligence”的显示文件夹中__。

    ![图片 4](Linked_image_Files/06-use-dax-time-intelligence-functions_image24.png)

1. 保存 Power BI Desktop 文件。

## 实验已完成
