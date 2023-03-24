# <!-- {docsify-ignore-all} -->

xray以proxy形式提供漏扫服务，你可以按照如下步骤使用服务

1. 下载安装证书

  证书信息见 [文件](https://github.com/leveryd-asm/asm/blob/master/templates/xray/config.yaml)

2. 浏览器配置代理

  代理地址一般是 `console.com:30088`，你也可以如下查询代理地址
  ```
  [root@192 ~]# kubectl get service -n asm | grep -i xray-proxy-service
  xray-proxy-service                NodePort    10.233.11.6     <none>        58088:30088/TCP              64d
  ```

3. 验证代理是否生效

4. 浏览目标网站

5. 在控制台运营漏洞

# 参考
[xray文档-代理模式进行扫描](https://docs.xray.cool/#/tutorial/webscan_proxy)

[asm项目v0.0.2版本总结](https://mp.weixin.qq.com/s/bGmL-XYXLxm3YxQt3sqCzw)
