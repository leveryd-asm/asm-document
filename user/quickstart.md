#

用户可以通过web页面管理资产、管理任务、运营报警。

# 访问控制台

在控制台上，你可以运营xray、nuclei报警，管理部分域名资产

* 怎么访问控制台？

  参考 [安装文档](ops/k8s.md) 的"步骤5：验证是否可以访问asm控制台"

  一般情况下，浏览器中输入 `http://console.com:32115/` 来访问控制台

# 访问argo-ui

在argo-ui上，你可以创建各类探测资产、漏洞扫描等任务，并且管理任务状态

* 怎么访问argo-ui？

  你可以在控制台上点击侧边栏访问到argo-ui

  ![](https://user-images.githubusercontent.com/1846319/225563172-53b313ec-e7a1-4fe5-acac-40ec664888de.png)

  或者浏览器输入 `http://asm控制台地址/argo` 地址，直接进入到argo-ui界面

# 访问kibana

通过kibana，你可以查看存入到elasticsearch中的各类数据，包括域名、端口、ip、web服务、爬虫数据等等信息

* 怎么访问kibana？

  绑定`kibana.console.com`host后，浏览器中输入 `http://kibana.console.com:32115/` 来访问kibana

# 访问xray-reverse管理页面
