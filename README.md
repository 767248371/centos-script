# 注意事项
## 1. 此脚本适用于Centos 7(最小化安装，无图形界面)，部分脚本内容包含Ubuntu下的用法，可根据实际情况进行变更
## 2. 脚本中涉及的IP地址和路径可以根据实际情况进行更改，但是有些路径是固定的，更改过后会出现问题，故在运行之前先了解一下工作原理
## 3. 脚本在运行过程中自带彩色字体输出，某些脚本执行一定流程过后需要手动操作，并非无人值守，请执行前先看一下执行步骤，涉及手动操作和其他命令的提示用黄色表示，密码提示等用红色表示

# 文件介绍
## 1. Base.sh
centos 基础环境配置，安装配置必备组件，包括(按照脚本执行顺序介绍)：

1.安装 *`wget`* --------------------------------------------------------------(后面很多工具要通过wget下载)，

2.更换 *`阿里源`* ------------------------------------------------------------------------(更快的下载速度)，

3.安装 *`nano`* ------------------------------------------------------------(文件编辑器，喜欢vim的可以不装)， 

4.安装 *`unzip`* --------------------------------------------------------------------------(zip解压工具)， 

5.安装 *`git`* ------------------------------------------------------------------------(代码版本控制工具)， 

6.安装 *`java`* --------------------------------------------------------------------------(程序员都懂得)， 

7.安装 *`yum-utils`* ----------------------------------------------------------------------(yum工具支持)， 

8.安装 *`expect`* ----------------------------------------------------------------(一个用来处理交互的命令)，

9.安装 *`htop`* ---------------------------------------------------------------(非常好用的系统资源监测工具)， 

10.安装 *`npm`* --------------------------------------------------------------------------(node包管理器)，

11.安装 *`pv`* ----------------------------------------------------------------------(复制文件显示进度条)， 

12.安装 *`telnet`* --------------------------------------------------------------------------(网络工具)，

13.安装 *`tree`* --------------------------------------------------------------------(显示文件夹树形结构)，

14.安装 *`pip`* ---------------------------------------------------------------------------(python2.7)， 

15.安装 *`supervisor`* -----------------------------------------------------(依赖Python2.7，进程管理工具)， 

16.安装 *`时间同步服务器`* -------------------------------------------------------(时间不同步连交流都很麻烦)，

17.关闭 *`swap分区`* 、

18.关闭并禁用 *`系统防火墙`* 、

19.关闭 *`SSH DNS反向解析和GSSAPI的用户认证`* --------------------------------------------(提升SSH连接速度)。

## 2. Docker&docker-compose
安装 *`Docker`* 和 *`docker-compose`*

## 3. Gitlab.sh
安装 *`Gitlab`* ，支持中文(登录过后在setting中设置语言即可)，设置包括：

1.安装 *`SSH `* ---------------------------------------------------(一般Linux都自带，支持SSH克隆或者提交代码)，

2.安装 *`邮件服务器`* --------------------------------------------------(git注册和找回密码合并代码等发送邮件用)，

3.安装 *`Gitlab 社区版`*

4.设置 *`定时任务，每天凌晨两点，执行gitlab备份`* 

5.设置 *`gitlab域名`* -----------------------------------------------------------------(形成正确的仓库连接)，

6.设置 *`备份保存时间，默认7天`* 

> 备份时间和备份保存时间可根据实际情况修改

## 4. MongoDB.sh
安装 *`MongoDB`* 数据库

> *`MongoDB`* 默认没有用户名和密码，可以用Navicat等数据库管理工具直接连接

## 5. MySQL.sh
安装 *`MySQL`* 数据库社区版，脚本主要设置了固定密码。

关于如何开启远程访问(centos 7下)：

1.登录进mysql
```
mysql -u root -p
```
2.更新表内容
```
grant all privileges on *.* to 'root' @'%' identified by '你的root用户密码’;
```
3.刷新权限
```
flush privileges;
```

## 6. RabbitMQ.sh
安装 *`RabbitMQ`* 消息通知

>访问端口号 *`16572`* ， 用户名 *`admin`*  ，密码 *`123456`* 

## 7. Supervisor.sh
通过 *`supervisor`* 进程管理工具设置应用程序开机自启动

> 上述 *`Base.sh`* 设置了 *`supervisor`* 的管理界面，端口号 *`9001`* ，用户名 *`admin`* ，密码 *`123456`* 

## 8. gitlab.rb
*`gitlab`* 配置文件，包含域名和备份设置(其他功能皆删除)

# 用法
很多工具的安装依赖 *`Base.sh`* 中涉及到的工具，故建议先执行Base.sh，再根据实际需求执行上述其他脚本

祝好运！