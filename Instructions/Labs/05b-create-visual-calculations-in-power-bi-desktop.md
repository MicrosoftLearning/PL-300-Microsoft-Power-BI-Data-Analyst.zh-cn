---
lab:
  title: 在 Power BI Desktop 中创建视觉计算
  module: Create Visual Calculations in Power BI Desktop
---

# 在 Power BI Desktop 中创建视觉计算

## **实验室场景**

在本实验室中，你将使用 Data Analysis Expressions (DAX) 创建视觉计算。 

本实验室介绍如何完成以下操作：

- 创建和编辑视觉计算
- 使用 PREVIOUS()、RUNNINGSUM() 和 MOVINGAVERAGE() 函数在每个会计年度之间创建比较指标
- 创建比较指标时，请使用可选的轴参数。
- 使用可选的重置参数自定义多级轴中的累积计算。

**此实验室应该大约需要 30 分钟。**

## 开始使用

若要完成本练习，请先打开 Web 浏览器并输入以下 URL 以下载 zip 文件夹：

`https://github.com/MicrosoftLearning/PL-300-Microsoft-Power-BI-Data-Analyst/raw/Main/Allfiles/Labs/05b-create-visual-calculations-in-power-bi-desktop/05b-visual-calculations.zip`

将文件夹解压缩到 **C:\Users\Student\Downloads\05b-visual-calculations** 文件夹。

打开 **05b-Starter-Sales Analysis.pbix** 文件。

> ***备注**：可以通过选择“取消”**** 来取消登录。 关闭所有其他信息窗口。 如果系统提示应用更改，请选择“稍后应用”****。*

## 创建 Power BI 条形图视觉对象

在此任务中，你将创建条形图，其中按财政年度显示销售额、总产品成本和利润，并将比较指标作为工具提示。

1. 在“**可视化**”窗格中，选择簇状条形图视觉对象类型。

   ![图片 01](Linked_image_Files/05b-create-visual-calculations-in-power-bi-desktop_image01.png)

1. 在“**数据**”窗格中，从“**日期**”表内，将“**年份**”字段拖入“**Y-轴**”井/区域中。

1. 将**销售**表中的“**销售**”和“**成本**”字段拖到 **X 轴**井/区域。

    > 请注意，向视觉对象添加“销售额和成本”时，会自动计算每个字段的总和。

1. 使用三点菜单按“**年份**”升序对生成的条形图进行排序，依次选择“**年份**”、**升序排序**：

   ![图片 02](Linked_image_Files/05b-create-visual-calculations-in-power-bi-desktop_image02.png)

    > 现在有一个条形图，显示按年份按时间顺序排序的销售总额和成本总额。

### 添加计算

1. 选中条形图后，在功能区中选择“**新建视觉计算**”：

   ![图片 03](Linked_image_Files/05b-create-visual-calculations-in-power-bi-desktop_image03.png)

1. 视觉计算编辑窗口打开。 在可视化矩阵上方的公式栏中，输入以下表达式，然后 Enter 提交计算：

    ```DAX
   Profit = [Sum of Sales] – [Sum of Cost]
    ```

1. 确认现在在屏幕底部的视觉矩阵上看到“利润”列：

   ![图片 04](Linked_image_Files/05b-create-visual-calculations-in-power-bi-desktop_image04.png)

1. 展开“**新建视觉计算**”下的菜单，从模板选项中选择“**与之前对比**”：

    > “**与之前对比**”将一个值与前一个值进行比较，因此我们看到了与之前“年份”值对比的“利润”。

   ![图片 05](Linked_image_Files/05b-create-visual-calculations-in-power-bi-desktop_image05.png)

1. 在公式栏中，将 `[Field]` 占位符替换为 `[Profit]` 两次并提交计算。

1. 从模板菜单中选择“**运行求和**”，并将 `[Field]` 占位符替换为 `[Profit]` 并提交计算。

    > **运行求和**计算值的总和，将当前值添加到前面的值，因此我们看到当前和之前年份的总和。

1. 从模板菜单中选择“**移动平均值**”，将 `[Field]` 占位符替换为 `[Profit]`并将 `WindowSize` 占位符替换为 2。 应具有以下设置：

    > **移动平均值**通过将值的总和除以窗口的大小，计算给定窗口中一组值的平均值。 通过将窗口大小设置为 2，我们将计算两个连续值的平均值。 在此示例中，这些值为年度利润，因此我们看到 2019 财年的移动平均值是 2018 财年和 2019 财年的利润平均值。

   ![图片 06](Linked_image_Files/05b-create-visual-calculations-in-power-bi-desktop_image06.png)

1. 在 **X 轴**井/区域下，选择以下字段的可见性图标，将其隐藏在视觉对象中：

    - 销售总额
    - 成本总和
    - Profit

   ![图片 07](Linked_image_Files/05b-create-visual-calculations-in-power-bi-desktop_image07.png)

    > 请注意，隐藏的字段和计算现在不再显示在视觉对象上。

1. 在“**可视化**”窗格中，将“**运行总和**”和“**移动平均值**”拖到“**工具提示**”井/区域。  

1. 确认视觉对象现在满足目标。 退出视觉计算编辑屏幕，进入报表：

   ![图片 08](Linked_image_Files/05b-create-visual-calculations-in-power-bi-desktop_image08.png)

    > 现在，有一个条形图包含以下值：销售总和、成本总和、利润、利润*与之前对比*，以及利润*运行总和*和利润*移动平均值*的工具提示。

## 创建矩阵视觉对象

在此任务中，将创建一个矩阵视觉对象，将每个类别的销售额与后续每一年的第一个会计年度进行比较。

1. 在**报表视图**中，新建一个报表页。

1. 在**第 2 页**上，添加一个矩阵视觉对象。

1. 将以下字段添加到视觉对象井/区域中：

    - 行：**产品 \| 类别**
    - 列：**日期 \| 年份**
    - 值：**销售 \| 销售**

    > *实验室使用速记表示法引用字段。它将如下所示：Date \| Year。* 在此示例中，Date 是表名称，Year 是字段名称。

### 添加计算

1. 选中矩阵后，选择功能区中的“**新建视觉计算**”。

1. 在视觉计算编辑窗口中，键入并保存以下计算：

    ```DAX
   Versus first = [Sum of Sales] - FIRST([Sum of Sales])
    ```

    > 请注意矩阵如何显示每个类别的销售额与第一个类别的销售额之间的差异。

1. 选择“**值**”井/区域中的字段“**与第一个对比**”，通过将轴参数的 ROWS 值添加到 FIRST 来更新计算：

    ```DAX
   Versus first = [Sum of Sales] - FIRST([Sum of Sales], ROWS)
    ```

    > 请注意，当 ROWS 是轴参数的默认值时，不会发生任何变化。

1. 将 ROWS 替换为 COLUMNS，并观察计算现在将每个类别的销售额与第一个会计年度进行比较：

   ![图片 11](Linked_image_Files/05b-create-visual-calculations-in-power-bi-desktop_image11.png)

    > 请注意“**总销售额**”的“**与第一个对比**”列如何返回零，而不是与第一个会计年度的差值。 **总销售额**与年度总和处于不同的层级，因此被视为该级别的第一列。

1. 退出视觉计算编辑屏幕，进入报表。

## 创建折线图视觉对象

在此任务中，将创建一个折线图，显示销售的运行总和。 此金额将在每个会计年度开始时重置。

1. 在**报表视图**中，新建一个报表页。

1. 在**第 3 页**上，添加折线图视觉对象。

1. 将以下字段添加到视觉对象井/区域中：

    - X 轴：**日期 \| 年份**和**日期 \| 季度**
    - Y 轴：Sales \| Sales

### 添加“运行总和”

1. 选中折线图后，展开“**新建视觉计算**”下的菜单，然后从模板选项中选择“**运行总和**”。

1. 将 `[Field]` 占位符替换为 `[Sum of Sales]` 并提交更改。 该视图对象应如下所示：

   ![图片 09](Linked_image_Files/05b-create-visual-calculations-in-power-bi-desktop_image09.png)

### 更新运行总和以重启每个新的会计年度

1. 在视觉计算编辑窗口中，选择 **Y 轴**下的“**运行总和**”字段，通过添加 HIGHESTPARENT 重置参数并提交更改来更新此计算的表达式：

    ```DAX
   Running sum = RUNNINGSUM([Sum of Sales], HIGHESTPARENT)
    ```

验证运行总和是否确实在每个新的会计年度重启：

   ![图片 10](Linked_image_Files/05b-create-visual-calculations-in-power-bi-desktop_image10.png)

## 实验已完成
