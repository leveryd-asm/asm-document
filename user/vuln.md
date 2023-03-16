#

# 怎么运营漏洞？
你可以在asm控制台上运营漏洞，处理过的漏洞可以标记成"无需处理"和"已处理"两种状态。

# 在企业微信上运营

如果你在安装本项目时有设置`weixin_webhook_url`参数，比如`helm --set weixin_webhook_url=https://qyapi.weixin.qq.com/cgi-bin/webhook/send?key=07d4613c-45ef-46e2-9379-a7b2aade3132`，xray扫描的漏洞就会通过webhook推送到企业微信群。
