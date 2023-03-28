#

# 4h8g配置的机器安装asm实例后，发现cpu资源好像满了，怎么办？

4h8g配置的机器，安装asm实例后，资源情况如下

![](https://user-images.githubusercontent.com/1846319/226093451-7e354e3a-d63c-4010-a255-63f22b3d3ca8.png)

elastcsearch、kibana、zoomkeeper 的 resource request值比较大。调小之后，会好一些。

![](https://user-images.githubusercontent.com/1846319/226095131-762c4a30-2c56-4f84-827e-f12b651d6f12.png)

> 参考issue [4h8g的机器安装一个asm实例后，cpu和内存的请求值就满了](https://github.com/leveryd-asm/asm/issues/36)

# 必须用域名才能访问控制台、kibana吗？

因为服务是通过[kubernetes ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/)暴露给集群外的用户，所以必须使用域名访问。

有可能你懒得绑定域名，或者你使用代理访问控制台时域名绑定失效了，你可以试试`nip.io`域名，参考 [k8s中使用ingress时的小技巧](https://mp.weixin.qq.com/s/aK7XWJ7h0smyAQOjWcRBaA)

# `helm dependency update` 更新时速度太慢了怎么办？

  helm 支持 http/https代理
  ```
  export http_proxy="http://代理"
  export https_proxy="https://代理"
  ```

# `helm dependency build` 报错

  提示添加仓库，如下
  ```
  [root@instance-i7xe5t04 asm]# helm dependency build
  Error: no repository definition for https://helm.elastic.co, https://helm.elastic.co. Please add the missing repos via 'helm repo add'
  ```

  你可以执行如下命令
  ```
  helm repo add bitnami https://charts.bitnami.com/bitnami
  helm repo add argo https://argoproj.github.io/argo-helm
  helm repo add elastic https://helm.elastic.co
  ```

# docker镜像拉取速度过慢

  配置registry-mirrors选项

  ```
  [root@192 leveryd]# cat /etc/docker/daemon.json
  {
    "log-opts": {
      "max-size": "5m",
      "max-file":"3"
    },
    "exec-opts": ["native.cgroupdriver=systemd"],
    "registry-mirrors": ["https://bdasxx8n.mirror.aliyuncs.com"]
  }
  ```

  然后 `service docker restart` 重启容器镜像服务
