# 水平扩容

asm项目运行在kubernetes集群上，因此你只要添加worker节点，编排引擎就会自动调度任务到各个节点上，实现水平扩展。

怎么添加worker节点呢？ 如果你是虚拟机安装的kubernetes，可以参考 [kubekey添加新节点](https://kubesphere.io/zh/docs/v3.3/installing-on-linux/cluster-operation/add-new-nodes/)。如果你是购买云上集群服务，云厂商基本都支持在控制台上增加worker节点，请参考云厂商文档。
