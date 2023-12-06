#

本文档帮助你安装kubernetes和asm。

> 目前asm服务大多没有实现身份认证，如果通过外网访问服务，建议做ip访问限制。

# 步骤1：准备kubernetes环境
* 硬件推荐配置

  4 核 CPU，8 GB 内存，80 GB 磁盘空间

* 安装kubernetes

  推荐你用[适用于国内网络环境的kubekey项目](https://github.com/kubesphere/kubekey/)安装kubernetes

  ```
  export KKZONE=cn
  ./kk create cluster --with-kubernetes v1.24.1 --container-manager containerd
  ```

* 安装kubesphere(虽然是可选步骤，但是k8s新手建议安装)

  kubesphere 可以用来管理k8s集群，并且提供了`ingress controller`。

  你可以按照如下命令安装`v3.3.1`版本。***安装前，你需要有默认StorageClass***，为什么以及怎么创建默认StorageClass可以见[这个issue](https://github.com/leveryd-asm/asm/issues/38)
  ```
  kubectl apply -f https://github.com/kubesphere/ks-installer/releases/download/v3.3.1/kubesphere-installer.yaml
  kubectl apply -f https://github.com/kubesphere/ks-installer/releases/download/v3.3.1/cluster-configuration.yaml
  ```

  > 详细安装步骤参考 [kubesphere](https://kubesphere.io/zh/docs/v3.3/quick-start/minimal-kubesphere-on-k8s/)，你也可以用[适用于国内网络环境的kubekey项目](https://github.com/kubesphere/kubekey/)快速安装kubernetes和kubesphere。

  如果你不需要kubesphere，可以使用`ingress-nginx`作为`ingress controller`。

# 步骤2：下载项目代码到本地

下载并切换到项目根目录
```
git clone https://github.com/leveryd-asm/asm --depth 1
cd asm/
```

# 步骤3：开始安装项目

第一次安装时，需要执行`helm dependency update`下载依赖。

> helm命令你可以在 [releases](https://github.com/helm/helm/releases) 页面下载

执行如下命令会创建asm命名空间，并在asm命名空间中安装本项目
```
kubectl create namespace asm
helm -n asm template ./ | kubectl apply -n asm -f -
```

你也可以向helm传递参数来修改安装的配置，如下命令会使用`asm-manage.com`作为域名访问控制台
```
helm -n asm template ./ --set console_domain=asm-manage.com  | kubectl apply -n asm -f -
```

# 步骤4：验证安装是否成功

查看pod状态是否都是running
```
kubectl get pod -n asm
```

# 步骤5：验证是否可以访问asm控制台

asm实例安装完成后，你就可以通过浏览器进入到asm控制台上管理资产、管理任务、运营报警

* 创建网关(ingress)

  如果你安装了kubesphere，就可以在kubesphere控制台上创建一个网关

  ![](https://user-images.githubusercontent.com/1846319/226091298-d13f5e7e-6d61-4648-bcb3-fdec2da96e92.png)

* 找到ingress的nodeport

  如果你安装了kubesphere，就可以执行如下命令，命令结果说明集群外可以访问 `节点ip:32115`
  ```
  [root@192 ~]# kubectl get pod -n kubesphere-controls-system | grep -i kubesphere-router-kubesphere-system
  kubesphere-router-kubesphere-system-5cfc84c77c-jh42b   1/1     Running   15         24d
  [root@192 ~]# kubectl get service -A | grep kubesphere-router-kubesphere-system
  kubesphere-controls-system     kubesphere-router-kubesphere-system           NodePort    10.233.44.102   <none>        80:32115/TCP,443:31474/TCP     95d
  ```

  或者在`kubesphere`控制台上找到`console` ingress访问地址，如下图所示

  ![](https://user-images.githubusercontent.com/1846319/209645921-d845c719-4f31-4e88-ae7c-c4326019b90a.png)
  ![](https://user-images.githubusercontent.com/1846319/209645971-34b5443c-bcd3-46a2-84a8-fa2378cbc9df.png)


* 绑定域名到节点ip

  控制台域名默认是`console.com`

  mac下的host文件路径在`/etc/hosts`，windows下的host文件路径在`C:\Windows\System32\drivers\etc\hosts`

  > 你也可以用 [SwitchHosts](https://github.com/oldj/SwitchHosts) 管理hosts文件

* 浏览器上访问asm控制台

  ![](https://user-images.githubusercontent.com/1846319/225215933-1a8bec34-c07e-4ce2-8d88-ee805e72796a.png)
