#

本文档帮助你安装kubernetes和asm。

# 步骤1：准备kubernetes环境
* 硬件推荐配置

  4 核 CPU，8 GB 内存，80 GB 磁盘空间

* 安装kubernetes

  推荐你用[适用于国内网络环境的kubekey项目](https://github.com/kubesphere/kubekey/)安装kubernetes

  ```
  ./kk create cluster --with-kubernetes v1.24.1
  ```

* 安装kubesphere(可选)

  kubesphere 可以用来管理k8s集群，并且提供了`ingress controller`。

  你可以按照如下命令安装`v3.3.1`版本
  ```
  kubectl apply -f https://github.com/kubesphere/ks-installer/releases/download/v3.3.1/kubesphere-installer.yaml
  kubectl apply -f https://github.com/kubesphere/ks-installer/releases/download/v3.3.1/cluster-configuration.yaml
  ```

  > 详细安装步骤参考 [kubesphere](https://kubesphere.io/docs/quick-start/minimal-kubesphere-on-k8s/)，你也可以用[适用于国内网络环境的kubekey项目](https://github.com/kubesphere/kubekey/)快速安装kubernetes和kubesphere。

  如果你不需要kubesphere，可以使用`ingress-nginx`作为`ingress controller`。

# 步骤2：下载项目代码到本地

下载并切换到项目根目录
```
git clone https://github.com/leveryd-asm/asm --depth 1
cd asm/
```

# 步骤3：开始安装项目

第一次安装时，需要执行`helm dependency update`下载依赖。

执行如下命令会在asm命名空间中安装本项目
```
helm -n asm template ./ | kubectl apply -n asm -f -
```

你也可以向helm传递参数来修改安装的配置，如下命令会使用`manage.com`作为域名访问控制台
```
helm -n asm template ./ --set console_domain=manage.com  | kubectl apply -n asm -f -
```

# 步骤4：验证安装是否成功

查看pod状态是否都是running
```
kubectl get pod -n asm
```

# 步骤5：验证是否可以访问asm控制台

asm实例安装完成后，你就可以通过浏览器进入到asm控制台上管理资产、管理任务、运营报警

* 找到ingress的nodeport

  如果你安装了kubesphere，就可以执行如下命令，说明集群外可以访问 `节点ip:32115`
  ```
  [root@192 ~]# kubectl get service -A|grep kubesphere-router-kubesphere-system
  kubesphere-controls-system     kubesphere-router-kubesphere-system           NodePort    10.233.44.102   <none>        80:32115/TCP,443:31474/TCP     95d
  ```

* 绑定域名到节点ip

  控制台域名默认是`console.com`

  mac下的host文件路径在`/etc/hosts`，windows下的host文件路径在`C:\Windows\System32\drivers\etc\hosts`

  > 你可以用 [SwitchHosts](https://github.com/oldj/SwitchHosts) 管理hosts文件

* 浏览器上访问asm控制台

  ![](https://user-images.githubusercontent.com/1846319/225215933-1a8bec34-c07e-4ce2-8d88-ee805e72796a.png)