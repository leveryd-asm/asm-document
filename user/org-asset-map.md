#

# 组织和资产的映射关系

用户可以修改[配置文件](https://github.com/leveryd-asm/asm/blob/master/templates/argo-workflow-template-asset/cron/org/config.yaml)，手动给资产打上对应组织的标签。

举例，语法如下
```
{ "org": "百度", "query": "subject_org:baidu OR subject_org:百度", "index": "tls" }
{ "org": "百度", "query": "title:baidu OR title:百度", "index": "web-service" }
{ "org": "百度", "query": "response-body:baidu OR response-body:百度", "index": "web-service" }
{ "org": "百度", "query": "parsed-domain.registered_domain:baidu.com", "index": "web-service" }
{ "org": "百度", "query": "asn.as-name:baidu OR asn.as-name:百度", "index": "web-service" }

# 主域名中包含baidu关键字
{ "org": "百度", "query": "parsed-domain.registered_domain.keyword :*baidu*", "index": "subdomain,port,web-service" }

{ "org": "百度", "query": "host.keyword:*.baidu.com", "index": "subdomain,port" }
{ "org": "百度", "query": "host.keyword:*.baidu.com.cn", "index": "subdomain,port" }
{ "org": "百度", "query": "domain.keyword:*.baidu.com", "index": "web-service" }
{ "org": "百度", "query": "domain.keyword:*.baidu.com.cn", "index": "web-service" }

```

# 怎么使映射关系生效？

步骤一：修改配置后重新部署asm实例

步骤二：立即更新 或 等待周期性更新

你可以立即执行`update-org-asset-map`工作流来更新资产所属

> asm实例中也会每两小时自动更新

步骤三：验证资产和组织是否映射成功

每类资产都有org和org_num两个字段，你可以在kibana上查看资产的org字段是否有值

# 参考
[asm项目v0.0.3版本总结](https://mp.weixin.qq.com/s/LOqioImlTnXitRq-CW9eXA)
