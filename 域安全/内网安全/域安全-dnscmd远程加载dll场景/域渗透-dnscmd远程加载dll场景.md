域渗透-dnscmd远程加载dll场景

 

1、复现过程

1）、生成payload

![1](./assets/1.jpg)

2）、开启smb服务端。

 ![2](./assets/2.jpg)

3)、利用dnscmd远程加载dll文件

![3](./assets/3.jpg)

 

4）、服务端文件传输成功

![4](./assets/4.jpg)

5）、重启dns服务器

![5](./assets/5.jpg)

6）、连接受害终端

![6](./assets/6.jpg)

7）、查看dns组册表项

 ![7](./assets/7.jpg)



 事件日志：

![8](./assets/8.jpg)



 ![9](./assets/9.jpg)

2、检测逻辑

 

event_id=1

（image以dnscmd.exe结尾 OR OriginaFileName:dnscmd.exe）AND commandline 以。DLL结尾

AND 

event_id = 13 

TargetObject: HKLM\System\CurrentControlSet\Services\DNS\Parameters\ServerLevelPluginDLL 

AND EventType: SetValue