---
lab:
  title: Power BI 中的安全数据访问
  module: Secure data access in Power BI
---

# Power BI 中的安全数据访问

## 实验室场景

在本实验室中，强制执行行级别安全性，确保销售人员只能分析向其分配的区域的销售数据。 你将使用动态方法强制实施行级别安全性。

**此实验室应该大约需要 20 分钟。**

## 开始使用

若要完成本练习，请先打开 Web 浏览器并输入以下 URL 以下载 zip 文件夹：

`https://github.com/MicrosoftLearning/PL-300-Microsoft-Power-BI-Data-Analyst/raw/Main/Allfiles/Labs/11-secure-data-access/11-secure-data.zip`

将文件夹提取到 C:\Users\Student\Downloads\11-secure-data 文件夹****。

打开 11-Starter-Sales Analysis.pbix 文件****。

> _注意****：文件加载时，可能会看到登录对话框。选择“取消”以关闭登录对话框。**** 关闭所有其他信息窗口。如果系统提示应用更改，请选择“稍后应用”****。_

## 强制执行行级别安全性

在此任务中，强制执行行级别安全性，确保销售人员只能看到向其分配的区域中的销售额。

1. 切换到“表”视图。****

   ![图片 5701](Linked_image_Files/11-secure-data-access_image20.png)

1. 在“数据”窗格中，选择“Salesperson (Performance)”表 。

1. 查看数据，会发现 Michael Blythe（EmployeeKey 为 281）的 UPN 值为**`michael-blythe@adventureworks.com`**
    
    > 回想一下，Michael Blythe 被分配到三个销售区域：美国东北部、美国中部和美国东南部。

1. 从“主页”**** 功能区选项卡上的“安全”**** 组中选择“管理角色”****。

    ![图片 5700](Linked_image_Files/11-secure-data-access_image21.png)

1. 在“管理安全角色”**** 窗口中的“角色”**** 部分中，选择“新建”****。

1. 在方框中，用角色名称替换选定的文本：“Salespeople”的名称，然后按 Enter。

   ![图片 5703](Linked_image_Files/11-secure-data-access_image23.png)

1. 要分配筛选器，请选择“销售人员（绩效）”**** 表，然后选择“筛选器数据”**** 部分中的“切换到 DAX 编辑器”****。

   ![图片 5703](Linked_image_Files/11-secure-data-access_image24.png)

1. 在“DAX 编辑器”框中，输入以下表达式：

    ```DAX
    [UPN] = USERPRINCIPALNAME()
    ```

   ![图片 11](Linked_image_Files/11-secure-data-access_image25.png)

    > USERPRINCIPALNAME () 是一种数据分析表达式 (DAX) 函数，它返回已经过身份验证的用户的名称。*这意味着，“Salesperson (Performance)”表将按查询模型的用户的用户主体名称 (UPN) 进行筛选。*

1. 选择“保存”和“关闭” 。

1. 要测试安全角色，请从“主页”**** 功能区选项卡的“安全”**** 组中，选择“查看者身份”****。

   ![图片 5708](Linked_image_Files/11-secure-data-access_image27.png)

1. 在“以角色身份查看”窗口中，勾选“其他用户”项，然后在相应的框中输入：**`michael-blythe@adventureworks.com`**

1. 选中“Salespeople”角色，然后选择“确定” 。
    
    > 完成此配置后，系统将使用“Salespeople”角色，并使用 Michael Blythe 的姓名扮演该用户。**

   ![图片 5709](Linked_image_Files/11-secure-data-access_image28.png)

1. 请注意报表页上面的黄色横幅，其中说明了测试安全性上下文。

   ![图片 13](Linked_image_Files/11-secure-data-access_image30.png)

1. 在表视觉对象中，请注意，仅列出了销售人员 Michael Blythe。

   ![图片 5713](Linked_image_Files/11-secure-data-access_image31.png)

1. 若要停止测试，请在黄色横幅的右侧，选择“停止查看”。

   ![图片 5712](Linked_image_Files/11-secure-data-access_image32.png)

1. 要删除**Salespeople** 角色，请在**主页**功能区选项卡上，从**安全**组中选择**管理角色**。

   ![图片 16](Linked_image_Files/11-secure-data-access_image33.png)

1. 在**管理安全角色**窗口中，选择**Salespeople** 角色上的省略号（...），然后选择“删除”****。 当看到确认删除的提示时，选择“是，删除”。

   ![图片 34](Linked_image_Files/11-secure-data-access_image34.png)

*备注：Power BI Desktop 文件发布到 Power BI 服务后，需要完成发布后的任务，以将安全主体映射到**销售员**角色。在本实验室中不执行此操作。*

## 实验已完成

可以选择保存 Power BI 报表，尽管此实验室不需要这样做。 

1. 关闭 Microsoft Edge 浏览器窗口。
1. 在 Power BI Desktop 中，导航到左上角的“文件”菜单，然后选择“另存为”。******** 
1. 选择“浏览此设备”。
1. 选择要在其中保存文件的文件夹，并为其指定描述性名称。 
1. 选择“保存”按钮，将报表另存为 .pbix 文件。**** 
1. 如果出现一个对话框，提示你应用挂起的查询更改，请选择“应用”。****
1. 关闭 Power BI Desktop。
