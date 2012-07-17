#Azure CMD

===========

## powershell

- 下载模块 最小安装模块 只安装azure shell支持
http://github.com/downloads/WindowsAzure/azure-sdk-tools/windowsazure-powershell.0.6.1.msi

- 启动
powershell.exe -NoExit -Command "cd 'C:\'; Get-ChildItem 'C:\Program Files\Microsoft SDKs\Windows Azure\PowerShell\Azure\*.psd1' | ForEach-Object {Import-Module $_}"

- 常用命令
help azure

Get-AzurePublishSettingsFile
获取账号设置，用于导入，建议用chrome设置默认浏览器，否则账号切换会有诡异问题

Import-AzurePublishSettingsFile
导入账号订阅设置

- 参考
https://www.windowsazure.com/en-us/develop/nodejs/how-to-guides/powershell-cmdlets/

##sqlcmd

- 版本至少2008及以上

- E:\Program Files\Microsoft SQL Server\100\Tools\Binn\SQLCMD.exe -U codesharp@g84etzrrzm.database.windows.net -P COOPERcooper5323210 -S g84etzrrzm.database.windows.net -d cooper

- 范例

use cooper

go

select * from cooper_account

go

- 自动化sql可用此工具