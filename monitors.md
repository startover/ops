#1.MRTG
mrtg（Multi Router Traffic Grapher）是一套用来绘出网络流量图的软件（通过snmp获取数据，通过web展示数据）；

##优点：
- 简单易上手，安装完简单改下配置文件就能用；

##缺点：
- 使用文本式数据库，调用不方便；
- 查看数据方式不够丰富，不可以自由地指定时间画图；
- 只能存两个DS（Data Source）-流量输入和输出；
- 取一次数据需绘图一次，浪费系统资源；
- 图像较模糊；
- 无用户、图像管理功能；
- 没有详细日志系统；
- 无法详细了解各流量的构成；
- 只能用于TCP/IP网络，对于SAN网络流量无能为力；
- 不能在命令行下工作。

#2.RRDTOOL
rrdtool是一个非常棒的画图工具(作者就是MRTG的作者)

##优点：
- 使用RRD（Round Robin Database）存储格式，数据等于放在数据库中，可方便调用（如将一个RRD文件中的数据与另一个RRD文件中的数据相加）
- 可定义任意时间段画图，可以用半年数据画一张图，也可以用半小时内的数据画一张图。
- 能画任意个DS，多种图形显示方式。
- 数据存储与绘图分开，减轻系统负载。
- 能任意处理RRD文件中的数据，如，在浏览监测中我们需要将数据由Bytes转化为bits，可以将原始数据乘8。

##缺点：
- RRDTool的作用只是存储数据和画图，它没有MRTG中集成的数据采集功能。
- 在命令行下的使用非常复杂，参数极多。
- 无用户、图像管理功能。

#3.Cacti
Cacti是一个用rrdtool画图的网络监控系统，集成了各种数据收集功能，在用rrdtool画出监控图像，界面很漂亮。

#4.Nagios
Cacti主要用于历史数据收集和画图，Nagios重点不在图形化监控，而在于监视大量服务器上面的大批服务是否正常，集成的报警功能比cacti强的多。
生产环境中通常是nagios+cacti组合的方式。
只是为了监控服务器/服务是否运行，nagios足矣；涉及画图的话，nagios+cacti通过NPC插件结合对接非常繁琐，调试ndo2db组件也会各种折腾，耗时费力，很明显没有zabbix包办报警+画图的方式靠谱。
另外，nagios半死不活的插件监控windows server什么的还是很痛苦的，zabbix的agentd在windows下则运行良好。

#5.Zabbix
zabbix是一个基于WEB界面的提供分布式系统监视以及网络监视功能的企业级的开源解决方案。能监视各种网络参数，保证服务器系统的安全运营;并提供柔软的通知机制以让系统管理员快速定位/解决存在的各种问题。

zabbix由zabbix server与可选组件zabbix agent2部分构成
- zabbix server可以通过SNMP，zabbix agent，ping，端口监视等方法提供对远程服务器/网络状态的监视，数据收集等功能，它可以运行在Linux, Solaris, HP-UX, AIX, Free BSD, Open BSD, OS X等平台之上。
- zabbix agent需要安装在被监视的目标服务器上，它主要完成对硬件信息或与操作系统有关的内存，CPU等信息的收集。zabbix agent可以运行在Linux ,Solaris, HP-UX, AIX, Free BSD, Open BSD, OS X, Tru64/OSF1, Windows NT4.0, Windows 2000/2003/XP/Vista)等系统之上。
- zabbix server可以单独监视远程服务器的服务状态;同时也可以与zabbix agent配合，可以轮询zabbix agent主动接收监视数据(trapping方式)，同时还可被动接收zabbix agent发送的数据(trapping方式)。
- 另外zabbix server还支持SNMP (v1,v2)，可以与SNMP软件(例如：net-snmp)等配合使用。

##zabbix的主要特点：

- 安装与配置简单，学习成本低
- 支持多语言(包括中文)
- 免费开源
- 自动发现服务器与网络设备
- 分布式监视以及WEB集中管理功能
- 可以无agent监视
- 用户安全认证和柔软的授权方式
- 通过WEB界面设置或查看监视结果
- email等通知功能

##Zabbix主要功能：
- CPU负荷
- 内存使用
- 磁盘使用
- 网络状况
- 端口监视
- 日志监视
