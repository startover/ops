##简介

系统集成了Node和Nginx等服务，适用于单核1G或更高配置ECS，是为弹性伸缩任务优化的镜像。

##功能列表

- 开机自动从Node-T1处同步最新代码  `onions/onionfp/NginxConfiguration`
- 代码拉取成功自动启动nginx和node  `node由PM2管理`
- 内置用于手动更新代码的可视化脚本 `auto-init-onions-v`

##更新日志

+ **Node4AS V2.1.0**  `2016-01-26 12:00`

  + 移除OneAPM监控服务
  + 更新阿里云监控服务
  + 更新镜像内代码版本

+ **Node4AS-V2.0.1**  `2016-01-19 15:00`

  + 更新代码和应用环境(npm install)。

+ **Node4AS-V2.0.0**  `2016-01-19 12:00`

  + 整合为单盘40G模式
  + 更新镜像内代码版本
  + 优化Nginx启动流程（同步完所有代码启动node成功后再启动Nginx）

+ **Node4AS-V1.0.0**  `2016-01-07 15:00`

  + 系统镜像Node4AS-SYS-SL
  + 数据快照Node4AS-DAT-SL
  + 20G+20G模式

+ **Node4AS-V0.5.0**  `2016-01-06 16:00`

  + 系统镜像Node4AS-SYS
  + 数据快照Node4AS-DAT
  + 20G+100G模式

##备注

系统镜像由原2.5版Node系统镜像删减进化而来。
