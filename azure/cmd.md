#Azure CMD

===========

## powershell

- ����ģ�� ��С��װģ�� ֻ��װazure shell֧��
http://github.com/downloads/WindowsAzure/azure-sdk-tools/windowsazure-powershell.0.6.1.msi

- ����
powershell.exe -NoExit -Command "cd 'C:\'; Get-ChildItem 'C:\Program Files\Microsoft SDKs\Windows Azure\PowerShell\Azure\*.psd1' | ForEach-Object {Import-Module $_}"

- ��������
help azure

Get-AzurePublishSettingsFile
��ȡ�˺����ã����ڵ��룬������chrome����Ĭ��������������˺��л����й�������

Import-AzurePublishSettingsFile
�����˺Ŷ�������

- �ο�
https://www.windowsazure.com/en-us/develop/nodejs/how-to-guides/powershell-cmdlets/

##sqlcmd

- �汾����2008������

- E:\Program Files\Microsoft SQL Server\100\Tools\Binn\SQLCMD.exe -U codesharp@g84etzrrzm.database.windows.net -P COOPERcooper5323210 -S g84etzrrzm.database.windows.net -d cooper

- ����

use cooper

go

select * from cooper_account

go

- �Զ���sql���ô˹���