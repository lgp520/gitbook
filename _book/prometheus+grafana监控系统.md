	监控对于业务系统的正常运行有着极其重要的作用，本文将介绍prometheus监控系统的原理、功能及部署流程。

## 简介

promethues是一套开源的监控告警系统，被越来越多的公司所接受，并于2016年加入CNCF。其系统架构如下：

![image-20200610162941696](/Users/liguopei/Library/Application Support/typora-user-images/image-20200610162941696.png)

## 能做什么？

**采集 **

prometheus的生态圈包含很多组件，能采集丰富、结构化的指标信息。包括但不限于服务器资源指标、k8s集群资源使用情况、数据库中间件的指标。例如：node-exporter、mysqld-exporter、kube-state-metrics等。采集组件会将采集到的结构化数据暴露给prometheus server主动拉去数据抓取，并存储到内部的时许数据库中。

**存储**

从采集器拉取到的指标存储在自带的时序数据库中，并作为grafana展示的数据源以及告警组件alertmanager告警依据。grafana以及prometheus UI通过PromQL查询存储在数据库指标。

**展示**





