mongodb实时监控工具，可以同时对多个MongoDB服务器进行监控。显示当前操作。

## 安装

motop是python编写的，可以使用pip安装

```
$ sudo pip install git+https://github.com/tart/motop.git
```

当然作者还提供了easy_install及本地安装等方式

## 使用

使用方法：

```
motop [-h] [-u USERNAME] [-p PASSWORD] [-c CONF] [-V] [-K AUTOKILLSECONDS]
      [host [host ...]]
```

通用选项：

- -h, --help					   帮助信息
- -u USERNAME，--username USERNAME		   用户名，认证用，默认空
- -p PASSWORD, --password PASSWORD		   密码，认证用，默认为空
- -c CONF, --conf CONF				   指定配置，默认/etc/motop.conf
- -V ,--version					   显示版本
- -K AUTOKILLSECONDS, --auto-kill AUTOKILLSECONDS  自动关闭时间，默认为空

- host 服务器地址或配置文件中的部件名称，默认是localhost:27017

动作介绍：

- q 退出
- p 暂停
- e 解释查询
- k 中止操作
- K 中止比给出时间耗时还大的操作
- r 尝试重新连接那些连接失败的服务器
- R 尝试重新连接所有服务器

依赖关系:

- python 2.6 及以上版本
- pymongo 2.0 及以上版本

配置文件(可选):

配置文件路径为 /etc/motop.conf.

配置文件可以含有多个部分，每部分都能包含如下语法：

address
Mongo服务器地址 (必写)
username
连接Mongo服务器的用户名
password
连接Mongo服务器的密码
status
显示状态，默认开启(on)
replicationInfo
显示复制集信息，默认on
replicaSet
显示replica set状态,默认on
operations
显示操作状态，默认on
replicationOperations
持续显示主从之间的复制集操作，默认开启

"DEFAULT" 是特殊部分，在此部分语法可以设成默认。

部分的名称将被作为服务器名称，这些名称同样可以用于命令执行。

示例配置:

```

[MongoDB01]
address=10.42.2.121
replicationOperations=off

[MongoDB02]
address=10.42.2.122

[MongoDB03]
address=10.42.2.123

[MongoDB04]
address=10.42.2.124
username=foo
password=bar

```
