在生产环境中需要实时监控Nginx服务器，然而不想安装部署Nagios、Zabbix或者Munin等复杂的监控软件，只求一种快速简便的办法去监控Nginx服务器的请求，ngxtop便成了我们的菜。

## 安装

ngxtop是python编写的，可以使用pip安装

```
$ sudo pip install ngxtop
```

## 使用

使用方法：

```
ngxtop [options]
ngxtop [options](print|top|avg|sum)<var>
ngxtop info
```

通用选项：

- -l:指定nginx或apache2日志文件的完整路径
- -f:日志格式
- -no-follow:不实时处理新添加到日志文件的日志，只处理当前已经写入的日志文件
- -t:更新频率
- -n:显示行号
- -o:排序规则（默认访问计数）
- -a...,-a...:添加表达式（一般是聚合表达式，如sum,avg,min,max等）到输出中
- -v:输出详细信息
- -i:之处理符合规则的记录

内置变量：

- bodybytessend
- http_referer
- httpuseragent
- remote_addr
- remote_user
- request
- status
- time_local

##### 监控Nginx

```
$ ngxtop
```
nginx默认会从配置文件中查找日志地址

##### 显示前20个最频繁的请求

```
$ngxtop -n 20
```

##### 获取Nginx基本信息
```
$ngxtop info
```

##### 自定义显示的变量
```
$ngxtop print request http_user_agent remote_addr
```

##### 显示请求最多的客户端IP地址

```
$ngxtop top remote_addr
```

##### 显示状态码是404的请求

```
$ngxtop -i 'status==404' print request status
```

##### 监控Apache服务器

```
$tail -f /var/log/apache2/access.log | ngxtop -f common
```
