# dataCollection
数据采集器

数据源(mysql binlog)(或者是业务日志)->日志解析器(解析binlog用canal，其他自定义)->mq(kafka)->数据库（es/redis）->前端展示(Kibana)
数据流向：Beats或自研系统上报日志到Kafka，然后Logstash从Kafka读取数据写入ES.Client，最终数据存放到ES.Data节点。用户可以通过Kibana或ES.Client的Restful接口查询数据。

(目前先做binlog+canal+kafka+es+kibana这一套流程)

其实我的预期是不管是cannal收集binlog还是logstash利用filebeat收集web日志，亦或者程序网关埋点统计用户行为，这些都是数据收集。
收集完了要放一个地方，通用方案是kafka。
关键是处理数据，目前俩个想法1.是结合用户画像做一个实时推荐系统，2.是简单的搭个es+kibana做个数据展示+索引。
然后推荐系统是根据海量数据来搞的，智能运算，分析一堆算法。感觉力有不逮，先做个2巩固一下，后期牛逼了再翻个1出来（滑稽）。

（我的一个小小的1核1G的百度云服务器根本搞不动啊，各种扣内存，以后要是有平台供自己发挥一定好好挥霍下（今天刚买了一个mac pro，本地搭起来搞搞））


qq交流群：java爱好编程群（452753966），加群备注 dc

## 前期准备
- mysql 开启bin-log日志
- cannal基础知识：安装canal服务端，写canal客户端代码
- kafka基础知识：会用api即可
- elasticsearch基础知识：会用api即可
- kibana基础知识：会用即可

## 项目意义
- 整合各个开源软件的过程，过一遍数据采集的流程，方便大家面试吹逼
- 可以用于解决mysql mq 发送一致性问题，避免硬编码；
- 可以进行日志分析（预警等）
- 可以进行数据异构（mysql支持查询的维度有限，可以将数据抽取到es中）

## 技术特点

没有特点，都是现有的开源框架，方案成熟。
自己搭一个出来，熟悉流程，方便以后面试吹逼

## 架构演进历史
数据抽取的演进：
1.  硬编码
2.  aop
3.  bin-log分析

## 博客地址：

目前自己是用有道笔记记录学习心得的，等后期整理了再统一放到网上。

## 常见问题答疑：

Q1:
A1:

