---
lab:
  title: 在 Power BI Desktop 中创建 DAX 计算
  module: Create Model Calculations using DAX in Power BI
---


# 在 Power BI Desktop 中创建 DAX 计算

## **实验室场景**

在本实验室中，使用数据分析表达式 (DAX) 创建计算表、计算列和简单的度量值。

本实验室介绍如何完成以下操作：

- 创建计算表
- 创建计算列
- 创建度量值

**此实验室应该大约需要 45 分钟。**

## **创建计算表**

在本练习中，你将创建两个计算表。 第一个是“Salesperson”表，允许它与“Sales”表之间有直接关系。 第二个是“Date”表。

重要说明：如果你是从上一个实验继续（并且已经成功完成该实验室），请不要完成此任务，而是从下一个任务开始继续操作。

1. 打开 Power BI Desktop。

    ![Power BI Desktop 图标](Linked_image_Files/02-load-data-with-power-query-in-power-bi-desktop_image1.png)

    提示：默认情况下，“入门”对话框在 Power BI Desktop 前面打开。可以选择登录，然后关闭弹出窗口。

1. 要打开 Power BI Desktop 入门文件，请选择“文件”>“打开报表”>“浏览报表”。

1. 在“打开”窗口中，导航到 D:\PL300\Labs\04-create-dax-calculations-in-power-bi-desktop\Starter 文件夹，并打开“Sales Analysis”文件  。

1. 关闭任何可能打开的信息窗口。

1. 请注意功能区下方的黄色警告消息。

    此消息提醒你查询尚未应用于加载为模型表这一事实。稍后将在此实验室中应用查询。

    要关闭该警告消息，请在黄色警告消息的右侧选择“X”。

1. 若要创建文件的副本，请转到“文件”>“另存为”，并保存到 D:\PL300\MySolution 文件夹 。

1. 如果系统提示应用更改，请选择“稍后应用”。

## **创建“Salesperson”表**

在此任务中，创建与 Sales 有直接关系的 Salesperson 计算表 。

计算表的创建方式为，先输入表名称，后面依次跟等于号 (=) 和返回表的 DAX 公式。 表名称不能是数据模型中已有的。

编辑栏支持输入有效的 DAX 公式。 它包括自动完成、Intellisense 和颜色编码等功能，让你能够快速、准确地输入公式。

1. 在 Power BI Desktop 中，在“报表”视图的“建模”功能区上，选择“计算”组中的“新建表”。

     ![图 1](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image9.png)

2. 在编辑栏（在创建或编辑计算时在功能区正下方打开）中，键入“Salesperson =”，按 Shift+Enter，键入“Salesperson (Performance)”，然后按 Enter。

    为了方便起见，可以从 D:\PL300\Labs\04-create-dax-calculations-in-power-bi-desktop\Assets\Snippets.txt 中的代码片段文件复制本实验室中的所有 DAX 定义**。

     ![图片 4](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image10.png)

     此表定义创建 Salesperson (Performance) 表的副本。它仅复制数据，但不复制如可见性、格式设置等模型属性。

     提示：建议输入“空格”（即回车和制表符）来以直观且易于阅读的格式编写公式，尤其在公式又长又复杂的情况下。要输入回车符，请按 Shift+Enter。“空格”是可选的。

1. 在“数据”窗格中，我们注意到，表图标为蓝色阴影（表示计算表）。

    ![图片 10](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image11.png)

    注意：计算表是使用返回表的 DAX 公式来定义的。请务必了解，计算表会增加数据模型的大小，因为它们会具体化和存储值。每当刷新公式依赖项时，都会对其进行重新计算，就像在此数据模型中将新（未来）日期值加载到表中时一样。

    与基于 Power Query 的表不同，计算表不能用于从外部数据源加载数据。它们只能根据已加载到数据模型中的内容来转换数据。

1. 切换到“模型”视图，请注意 Salesperson 表可用（可能需要重置视图以查找表）。

1. 创建从“Salesperson \| EmployeeKey”列到“Sales \| EmployeeKey”列的关系 。

1. 右键单击“Salesperson (Performance)”与“Sales”表之间的非活动关系，然后选择“删除”。 当看到确认删除的提示时，选择“是”。

1. 在“Salesperson”表中，选择以下列，然后将其隐藏（将“隐藏”属性设置为“是”）：

    - EmployeeID
    - EmployeeKey
    - UPN

1. 在模型图中，选择“Salesperson”表。

1. 在“属性”窗格的“说明”框中，输入：与销售额相关的销售员
    
    回想一下，当用户将光标悬停在表或字段上时，描述将显示为“数据”窗格中的工具提示。**

1. 对于“Salesperson (Performance)”表，将说明设置为：销售人员与一个或多个区域相关

数据模型现在会在分析销售人员时提供两种替代方案。 *“Salesperson”表可便于分析销售人员的销售额，而“Salesperson (Performance)”表则可便于分析分配给销售人员的一个或多个销售区域中的销售额。 *

## **创建“Date”表**

在此任务中，你将创建“Date”表。

1. 切换到“数据”视图。 在“主页”功能区选项卡上，选择“计算”组中的“新建表”。

    ![图片 5](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image15.png)

1. 在公式栏中，输入以下内容：

    **DAX**

    ```
    Date =  
    CALENDARAUTO(6)
    ```

    ![图片 6](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image16.png)


    CALENDARAUTO() 函数返回一个由日期值组成的单列表。 *“自动”行为扫描所有数据模型日期列，以确定存储在数据模型中的最旧和最新日期值。* 然后，它为此范围内的每个日期都创建一行，并在两个方向上扩展此范围，以确保存储全年的数据。

    此函数可以采用一个可选参数，该参数表示一年的最后一个月。*如果省略，则值为“12”，表示 12 月是一年的最后一个月。* 在此示例中，输入“6”，表示 6 月是一年的最后一个月。

1. 注意包含日期值的列。

    ![图片 7](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image17.png)

    *显示的日期使用美国区域设置（即 mm/dd/yyyy）进行格式设置。*

5. 在左下角的状态栏中，我们注意到表统计信息确认生成了 1826 行数据，这代表五个全年的数据。

    ![图片 9](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image18.png)

## **创建计算列**

在此任务中，添加其他列，以支持按不同时间段进行筛选和分组。 你还将创建一个计算列来控制其他列的排序顺序。

为了方便起见，可以从 D:\PL300\Labs\04-create-dax-calculations-in-power-bi-desktop\Assets\Snippets.txt 中的代码片段文件复制本实验室中的所有 DAX 定义**。

1. 在“表工具”关联功能区上，选择“计算”组中的“新建列”。

    ![图片 11](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image19.png)

1. 在公式栏中键入以下内容（或从代码片段文件中复制），然后按 Enter：


    **DAX**


    ```
    Year =
    "FY" & YEAR('Date'[Date]) + IF(MONTH('Date'[Date]) > 6, 1)
    ```


    计算列的创建方式为：先输入列名，后面依次是等号 (=) 和返回单值结果的 DAX 公式。该列名不能已存在于表中。

    此公式使用日期的年份值，但如果月份是在 6 月后，则会在年份值上加 1。这就是 Adventure Works 会计年度的计算方式。

1. 验证新列是否已添加。

    ![图片 12](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image20.png)

1. 使用代码片段文件定义为“Date”表创建以下两个计算列：

    - Quarter
    - Month

    ![图片 14](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image21.png)

1. 若要验证计算，请切换到“报表”视图。

1. 若要创建新的报表页，请选择“第 1 页”旁边的加号图标。

    ![图片 15](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image22.png)

1. 若要将矩阵视觉对象添加到新的报表页，请在“可视化效果”窗格中选择矩阵视觉对象类型。

    *提示：* 可以将光标悬停在每个图标上，以查看描述视觉对象类型的工具提示。

    ![图片 51](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image23.png)

1. 在“数据”窗格中，从“Date”表内，将“Year”字段拖入“行”井/区域中   。

    ![图片 17](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image24.png)

1. 将“Month”字段拖入“Year”字段正下方的“行”井/区域。

    ![图片 18](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image25.png)

1. 在矩阵视觉对象的右上角（或底部，取决于视觉对象的位置），选择“叉状双箭头”图标（可将所有年份向下展开一个级别）。

    ![图片 19](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image26.png)

1. 我们注意到，年份展开到月份，月份是按字母顺序排序，而不是按时间顺序排序。

    ![图片 20](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image27.png)

    *默认情况下，文本值按字母顺序排序，数字按从小到大的顺序排序，日期按从早到晚的顺序排序。*

1. 若要自定义“Month”字段排序顺序，请切换到“数据”视图。

1. 将“MonthKey”列添加到“Date”表中。


    **DAX**


    ```
    MonthKey =
    (YEAR('Date'[Date]) * 100) + MONTH('Date'[Date])
    ```


    *此公式会为每个年份/月份组合计算一个数值。*

1. 在“数据”视图中，验证新列是否包含数值（例如，201707 表示 2017 年 7 月等）。

    ![图片 21](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image28.png)

1. 切换回“报表”视图。 在“数据”窗格中，确保已选中“Month”字段（如果选中，则有深灰色背景）。

1. 在“列工具”关联功能区上，选择“排序”组中的“按列排序”，然后选择“MonthKey”。

    ![图片 22](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image29.png)

1. 在矩阵视觉对象中，我们注意到，月份现在按时间顺序排序。

    ![图片 23](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image30.png)

## 完成“Date”表

在此任务中，你将通过隐藏列和创建层次结构来完成“Date”表的设计。 然后，你将创建与“Sales”和“Targets”表的关系。

1. 切换到“模型”视图。 在“Date”表中，隐藏“MonthKey”列（将“隐藏”设置为“是”）。


1. 在“数据”右侧窗格中，选择 Date 表，右键选择“Year”列，然后选择“创建层次结构”   。 

1. 右键选择“重命名”，将新创建的层次结构重命名为“Fiscal” 。


1. 通过在“数据”窗格中选择其余两个字段，右键单击，选择“添加到层次结构”“Fiscal”，将其添加到“Fiscal”层次结构。  -> 

    - Quarter
    - Month

    ![图片 24](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image31.png)

1. 创建以下两个模型关系：

    - 从“Date \| Date”到“Sales \| OrderDate”
    - 从“Date \| Date”到“Targets \| TargetMonth”

1. 隐藏以下两列：

    - Sales \| OrderDate
    - Targets \| TargetMonth

## **标记日期表**

在此任务中，你将把“Date”表标记为日期表。

1. 切换到“报表”视图。 在“数据”窗格中，选择“Date”表（不是“Date”字段）。

1. 在“表工具”关联功能区上，选择“日历”组中的“标记为日期表”，然后选择“标记为日期表”。

    ![图片 8](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image32.png)

1. 在“标记为日期表”窗口中，选择“日期列”下拉列表中的“日期”。 选择“确定”。

    ![图片 37](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image33.png)

1. 保存 Power BI Desktop 文件。

    Power BI Desktop 现在知道此表定义的是日期（时间）。依靠时间智能计算时，这一点很重要。“在 Power BI Desktop 中创建高级 DAX 计算”实验室中将使用时间智能计算。

    这种日期表设计方法适用于数据源中没有日期表的情况。如果有数据仓库，应该从其日期维度表（而不是数据模型中的“重新定义”日期逻辑）中加载日期数据。

## **创建简单的度量值**

在此任务中，你将创建简单的度量值。 简单的度量值聚合单个列中的值或对表中的行进行计数。

1. 在“报表”视图“第 2 页”上的“数据”窗格中，将“Sales \| Unit Price”字段拖到矩阵视觉对象。

    *实验室使用速记表示法引用字段。它将如下所示：Sales \| Unit Price。在此示例中，Sales 是表名称，Unit Price 是字段名称。 *

    ![图片 27](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image35.png)

    回想一下，在“在 Power BI Desktop 中为数据建模”实验室中，你将“Unit Price”列设置为按“平均值”汇总。*  *你在矩阵视觉对象中看到的结果是每月平均单位价格（单位价格值的总和除以单位价格计数）。

1. 在视觉对象“字段”窗格（位于“可视化效果”窗格之下）的“值”字段井/区域，注意“Unit Price”已列出。

    ![图片 28](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image36.png)

1. 选择“Unit Price”的向下箭头，然后注意可用的菜单选项。

    ![图片 30](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image37.png)

    借助可见数值列，报表作者可以在设计报表时确定汇总（或不汇总）列值的方式。这可能会生成不当的报表。但是某些数据建模人员不喜欢碰运气，他们选择隐藏这些列，而不是公开度量值中定义的聚合逻辑。这就是你要在本实验室中采用的方法。

1. 若要创建度量值，请在“数据”窗格中右键单击“Sales”表，然后选择“新建度量值”。

1. 在编辑栏中，添加以下度量值定义：


    **DAX**


    ```
    Avg Price =  
    AVERAGE(Sales[Unit Price])
    ```

1. 将“Avg Price”度量值添加到矩阵视觉对象。

1. 我们注意到，它生成的结果与“Unit Price”列相同（但格式不同）。

1. 在“值”井中，打开“Avg Price”字段的上下文菜单，可以注意到无法更改聚合技术 。

    ![图片 32](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image39.png)

    无法修改度量值的聚合行为。

1. 使用代码片段文件定义为“Sales”表创建以下五个度量值：

    - Median Price
    - Min Price
    - Max Price
    - Orders
    - Order Lines

    “Orders”度量值中使用的 DISTINCTCOUNT() 函数只会对订单进行一次计数（忽略重复项）。*“Order Lines”度量值中使用的 COUNTROWS() 函数对表执行运算。*

    在此示例中，订单数是通过统计非重复“SalesOrderNumber”列值来计算的，而订单行数则就是表行数（每行都是一个订单行）。**

10. 切换到“模型”视图，然后选择四个价格度量值：“Avg Price”、“Max Price”、“Median Price”和“Min Price”。

11. 对于选择的多个度量值，配置以下要求：

    - 将格式设置为两位小数

    - 分配到名为“Pricing”的显示文件夹

    ![图片 33](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image40.png)

12. 隐藏“Unit Price”列。

    报表作者现在无法使用“Unit Price”列。*他们必须使用你添加到模型中的定价度量值。* 这种设计方法可确保报表作者不会以不当的方式对价格进行聚合（例如，通过对价格进行求和）。

13. 同时选择“Order Lines”和“Orders”度量值并配置以下要求：

    - 设置使用千位分隔符的格式

    - 分配到名为“Counts”的显示文件夹

    ![图片 36](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image41.png)

14. 在“报表”视图中，在矩阵视觉对象的“值”井/区域中，选择“Unit Price”字段的“X”以将其移除  。

    ![图片 38](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image42.png)

15. 增加矩阵视觉对象的大小，以占满报表页的宽度和高度。

16. 在“矩阵”视觉对象中添加以下五个新度量值：

    - Median Price
    - Min Price
    - Max Price
    - Orders
    - Order Lines

17. 验证结果是否合理，以及格式是否正确。

    ![图片 39](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image43.png)

## **创建其他度量值**

在此任务中，创建使用更复杂表达式的其他度量值。

1. 在“报表”视图中，选择“第 1 页”并查看表视觉对象，注意“Target”列的总计 。

    ![图片 41](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image45.png)


1. 选择表视觉对象，然后在“可视化效果”窗格中，删除“Target”字段。

1. 将“Targets \| Target”列重命名为“Targets \| TargetAmount” 。

    提示：有多种方法可以在“报表”视图中重命名列：在“数据”窗格中，右键单击相应的列，然后选择“重命名”；或双击相应的列；或按 F2*  *。

    你将要创建名为“Target”的度量值。** 同一个表中不能有同名的列和度量值。

1. 在“Targets”表上创建以下度量值：

    **DAX**


    ```
    Target =

    IF(

    HASONEVALUE('Salesperson (Performance)'[Salesperson]),

    SUM(Targets[TargetAmount])

    )
    ```

    HASONEVALUE() 函数测试是否在“Salesperson”列中筛选出单个值。*如果为 true，则表达式返回目标额总和（仅针对此销售人员）。* 如果为 false，则返回 BLANK。

1. 将“Target”度量值的格式设置为没有小数位。

    *提示：* 可以使用“度量值工具”上下文功能区。

1. 隐藏“TargetAmount”列。

    提示：在“数据”窗格中，可以右键单击该列，然后选择“隐藏”* *。

1. 将“Target”度量值添加到表视觉对象。

1. 我们注意到，“Target”列总计现在为 BLANK。

    ![图片 43](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image47.png)

1. 使用代码片段文件定义为“Targets”表创建以下两个度量值：

    - Variance
    - Variance Margin

1. 将“Variance”度量值的格式设置为没有小数位。

1. 将“Variance Margin”度量值的格式设置为，有两位小数的百分比。

1. 将“Variance”和“Variance Margin”度量值添加到表视觉对象。

1. 重设表视觉对象的大小，以便查看所有列和行。

    ![图片 44](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image48.png)

    虽然看上去所有销售员都未达到目标，但请记住，尚未按特定时间段对表视觉对象进行筛选。“在 Power BI Desktop 中设计报表”实验室中按用户所选的时间段进行筛选，以生成销售绩效报表。

1. 在“数据”窗格的右上角，折叠后展开，以打开此窗格。

    折叠并重新打开此窗格会重置内容。

1. 我们注意到，“Targets”表现在显示在列表的最上面。

    ![图片 46](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image50.png)

    *只包含可见度量值的表会自动在列表的最上面列出。*

### **完成**

保存 Power BI Desktop 文件。

“在 Power BI Desktop 中创建高级 DAX 计算”实验室中使用 DAX 生成更高级的计算，以便增强数据模型。
