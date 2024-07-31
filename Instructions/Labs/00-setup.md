---
lab:
  title: 设置自己的环境
  module: Set up your own environment
---

# 设置本地实验室环境

理想情况下，应在托管实验室环境中完成这些实验室。 如果要在你自己的计算机上完成它们，可以通过安装以下软件来完成。

- 可以[从 GitHub 下载](https://github.com/MicrosoftLearning/PL-300-Microsoft-Power-BI-Data-Analyst/raw/Main/AllfilesDownload.zip)所有安装程序和资源文件。
  - 将 'AllFiles' 文件夹提取到 D:/，并将其重命名为 'D:\Allfiles\'。

***使用自己的环境时，可能会出现意外的对话框和行为。由于本地配置层出不穷，课程团队无法为你在自己环境中可能遇到的问题提供支持。***

## 关于使用 Windows 11 的说明

> &#128221; 以下说明适用于 Windows 11 计算机。 从其他 OS 进行连接时，体验可能会有所不同。

### Power BI Desktop

1. 从 Microsoft Store 下载并安装。 如果你无权访问 Microsoft Store，请从 [Web](https://www.microsoft.com/download/details.aspx?id=58494) 下载。 Power BI Desktop 是这些实验室中的主要应用程序。

    - 使用安装程序中的默认选项。

### M365 开发者帐户

在部分练习中，需要使用组织帐户登录 Power BI。 可以使用自己的帐户，但如果没有访问权限，可以创建免费的 [M365 开发者帐户](https://developer.microsoft.com/en-us/microsoft-365/dev-program)。

### SQL Server 数据库引擎

1. 实验室连接到 localhost SQL Server 实例。 以下说明将帮助你安装 SQL Server 并配置默认选项。 只需安装数据库引擎功能。

    - 请下载免费的[安装介质的开发者副本](https://www.microsoft.com/sql-server/sql-server-downloads?SilentAuth=1&f=255&MSPPError=-2147217396&rtc=1)
    - [使用安装向导安装 SQL Server（安装程序）](https://learn.microsoft.com/sql/database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup)

> &#128221;如果具有访问权限，可以使用现有的 SQL Server 实例，而无需安装本地版本。 但需要将连接字符串从“localhost”修改为你自己的实例名称。

### Microsoft Edge

1. 安装最新版本的 [Microsoft Edge](https://microsoft.com/edge) 以在线访问 Power BI 服务。
