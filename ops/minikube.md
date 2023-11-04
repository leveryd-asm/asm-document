和 [kubernetes环境中安装](/ops/k8s) 步骤几乎一样

区别在于，minikube环境中，需要执行 `sudo ip link set docker0 promisc on` 命令

> 原因是minikube默认情况下pod无法访问自身service，见 [Pod unable to reach itself through a service (unless --cni=true is set)](https://github.com/kubernetes/minikube/issues/1568)

# 问题一：socat和conntrack依赖

如果你遇到以下报错，可以执行`yum install -y conntrack socat`安装依赖

<img width="1304" alt="image" src="https://github.com/leveryd-asm/asm-document/assets/1846319/a4b80955-c70b-4806-90de-f40a2b35011f">
