---
demo:
  title: 在 Power BI 中强制实施行级别安全性
  module: Deploy and manage Power BI service items
---

# 在 Power BI 中强制实施行级别安全性

## 在模型中添加安全性表

1. 在 Power BI Desktop 中，打开 Power Query 编辑器窗口。

1. 添加基于 `D:\Demo\Data\**ManagerCategory**.xlsx` 文件的新查询。

1. 使用文件中的 ManagerCategory 表。

1. 删除“管理员”列****。

1. 用分号分隔符将“**类别**”列拆分为行（高级选项）。

1. 在“电子邮件”列中，将值 <ty-johnston@tailspintoys.com> 替换为收件人帐户（来自 MySettings.txt 文件） 。

1. 指出该用户能够看到三个产品类别：可变螺距直升机、教练机和作战飞机。

1. 关闭并应用查询。

1. 在“模型”视图中，在与“类别”列相关的 ManagerCategory 表和 Product 表之间创建一个关系 。

1. 将交叉筛选方向设置为“单向(ManagerCategory 筛选 Product)”。

1. 隐藏 ManagerCategory 表****。

## 添加角色

1. 在“报表”视图中，打开“管理角色”，然后创建一个名为“管理员”的角色。

1. 在角色中筛选 ManagerCategory 表的“电子邮件地址”列，如下所示：

  ```dax
   [Email] = USERPRINCIPALNAME()
   ```

1. 保存。

## 验证角色

1. 打开“查看方式”，然后配置以下设置：

    - 其他用户：选中，然后输入收件人帐户。

    - 管理员角色：选中

1. 指出筛选视觉对象仅显示三个产品类别。

1. 使用“查看方式”选项停止查看报表。

1. 保存 Power BI Desktop 文件。

1. 将 Power BI Desktop 文件发布到工作区，从而覆盖服务中的语义模型和报表。

1. 关闭 Power BI Desktop。

## 配置语义模型安全性

1. 在适用于讲师的 Power BI 服务中，从“导航”窗格打开“销售分析”**** 语义模型的“安全性”页。

1. 在“成员”部分，输入收件人帐户（代表 Ty Johnston）。

1. 添加并保存。

## 在应用中测试行级别安全性

1. 在适用于收件人的 Power BI 服务中，刷新仪表板（在上一个演示中保持打开状态）。

1. 在“利润率”仪表板磁贴中，确认只能看到三个产品类别。
