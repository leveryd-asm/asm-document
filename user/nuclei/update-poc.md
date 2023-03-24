#

# 自动更新

每隔两小时，asm项目会从以下地址获取poc并更新：
* https://github.com/projectdiscovery/fuzzing-templates
* https://github.com/projectdiscovery/nuclei-templates

> 你可以从 [这里](https://github.com/leveryd-asm/asm/blob/master/templates/nuclei-template-update/util.yaml) 看到数据源

# 添加自定义poc
如果你想添加自己的私人poc，就需要挂载pv到容器目录后更新，具体步骤如下。

第一步：在argo-ui中启动容器

<img src="https://user-images.githubusercontent.com/1846319/225656905-ecb765be-1024-48f3-935c-2cc4d561b732.png" width="200px">

第二步：找到pod名称

```
[root@192 ~]# kubectl get pods -n asm | grep -i util-update-nuclei
util-update-nuclei-template-mnl8k                                            2/2     Running       0          143m
```

第三步：将poc拷贝到容器中
```
[root@192 ~]# kubectl cp test_poc.yaml util-update-nuclei-template-mnl8k:/root/nuclei-templates/ -n asm
```

第四步：验证poc拷贝是否成功
```
[root@192 ~]# kubectl exec util-update-nuclei-template-mnl8k -n asm -ti -- sh
/ # ls /root/nuclei-templates/ | grep test_poc.yaml
test_poc.yaml
```
