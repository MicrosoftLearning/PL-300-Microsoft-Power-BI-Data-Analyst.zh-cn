---
demo:
  "\_\_ title": Manage files and datasets in Power BI
  "\_\_ module": Deploy and manage Power BI service items
---
# 在 Power BI 中管理文件和数据集

## 准备网关数据刷新

> 注意：在个人模式下使用数据网关时，不需要执行以下步骤。 可以直接进行下一个目标（设置网关）。

1. 在 Power BI Desktop 中，打开 Power Query 编辑器窗口，然后选择“ProductCost”查询****。

1. 编辑“源”步骤，然后修改文件路径以使用文件共享，如下所示：

    `\\DATA-AI\Data\ProductCost.xlsx`

1. 关闭并应用 Power Query 编辑器窗口。

1. 保存 Power BI Desktop 文件。

1. 将 Power BI Desktop 文件发布到工作区，从而覆盖服务中的数据集和报表。

## 设置网关（个人模式）

1. 在适用于讲师的 Power BI 服务中，重新加载 (F5)“数据集设置”页面。

1. 展开“网关连接”部分，并指出未安装网关。

1. 使用下载下拉列表（位于右上角），然后选择“数据网关”。

1. 在新的网页中，下载个人模式网关。

1. 下载后，打开已下载的文件。

1. 使用讲师帐户的凭据完成网关设置。

1. 设置完成后，返回并重新加载数据集设置页面。

1. 分配个人网关，然后编辑两个数据源的凭据。

1. 对于这两个数据源，将身份验证方法设置为“WindowsWithoutImpersonation”，并将隐私级别设置为“Organizational”********。

1. （可选）展开“计划的刷新”部分，并显示如何配置定期计划****。

## 刷新数据集

1. 刷新数据集之前，请打开“销售额监视”仪表板****。

1. 编辑“销售额、利润率”磁贴的详细信息以显示上一次刷新时间。

1. 右键单击 `D:\PL300\Demo\Resources\UpdateDatabase-LoadAdditionalSales.ps1` 文件，然后使用 PowerShell 运行。 此脚本会将 2020 年 12 月的销售额数据加载到数据库中。

1. 在适用于讲师的 Power BI 服务中，在导航窗格中刷新“销售额分析”数据集。

1. 刷新完成后，请指出仪表板磁贴“2020 年 12 月”列的显示方式，以及刷新时间为“现在” 。