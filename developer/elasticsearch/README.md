# <!-- {docsify-ignore-all} -->

当前有六个索引

| 索引名 | 用途 |
| - | - |
| tls       | 证书
| subdomain | 子域名
| port      | 服务信息
| web-service | web首页
| favicon   | favicon.ico图标
| proxify   | 爬虫获取的api、html等

每个索引都会有一个first_create_time和last_update_time字段，分别表示文档第一次创建的时间和最近一次被更新的时间。这个时间字段可以用来发现新增的资产、过期的数据。

每个索引也通过文档id做了去重，比如证书资产以domain_ip_port去重

每类资产都有org和org_num两个字段，org是字符串数组类型，存放组织标签信息，所以一个资产可以标记成多个组织拥有。

# 怎么实现数据写入？

pd组织的工具和elk结合起来很容易实现资产探测和入库：httpx、naabu、tls、subfinder等工具都支持json输出，logstash将json数据导入到elasticsearch中。

> 实现资产导入的logstash配置见 [代码](https://github.com/leveryd-asm/asm/blob/master/templates/argo-workflow-template-asset/level1/logstash/config.yaml)
