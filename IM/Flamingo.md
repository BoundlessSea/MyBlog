# 介绍
Flamingo IM 是一款高性能、轻量级的开源即时通讯软件，目前包括服务器端、pc 端、安卓端，微信版本和 IOS 版本目前正在开发中。

参考：[项目自述](https://github.com/balloonwj/flamingo#readme) 。

## 编译和安装
### 服务器端的编译与安装
#### 依赖的开发工具

1.安装cmake、makefile和gcc。
​作系统是 Linux，推荐的版本是 CentOS 7.0 以上。服务器代码使用纯C++11开发，所以您的gcc/g++版本必须至少在4.7以上，推荐的版本是4.8.5。另外，使用cmake和makefile工具进行项目管理和编译，因此您需要安装cmake和makefile工具。

2.安装 mysql。

使用的数据库是mysql，如果您使用的是CentOS 7.0及以上系统，需要安装 mariadb-server、mariadb-client 和 mariadb-devel。如果您使用的是其他版本的linux系统，请安装 mysql-server、mysql-client 和 mysql-devel。

聊天服务 chatserver 会使用到 mysql，mysql 的库名（默认库名叫 flamingo）、登陆用户名和密码配置在 flamingoserver/etc/chatserver.conf 文件中。

首次启动聊天服务chatserver时，程序会自动检测是否存在flamingo这样的库，如果不存在则创建之，并检测相应的数据表是否存在，如果不存在则创建它们。所以，无需手动创建对应的库和表。当然，不排除由于不同的mysql版本对应的SQL语法有细微差别，可能建表会失败，这个时候你可能需要手动建表，建表语句在flamingoserver/table.sql中。flamingo目前使用的四个表分别是：

表名	用途说明
t_user	用户信息表
t_user_relationship	好友关系及群成员信息表
t_chatmsg	聊天记录表
