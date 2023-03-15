和 [kubernetes环境中安装](/ops/k8s) 步骤几乎一样

区别在于，minikube环境中，需要执行 `sudo ip link set docker0 promisc on` 命令

> 原因是minikube默认情况下pod无法访问自身service，见 [Pod unable to reach itself through a service (unless --cni=true is set)](https://github.com/kubernetes/minikube/issues/1568)
