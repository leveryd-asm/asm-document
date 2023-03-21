# <!-- {docsify-ignore-all} -->

# 什么是应用？

在leveryd-asm项目中，`level1`工作流模板就是应用。它是原子能力，目前分为"资产"和"漏洞"两大类。

"资产"相关的应用使用到的工具包括：
- [fofax](https://github.com/xiecat/fofax)
- [nuclei](https://github.com/projectdiscovery/nuclei)
- [httpx](https://github.com/projectdiscovery/httpx)
- [naabu](https://github.com/projectdiscovery/naabu)
- [katana](https://github.com/projectdiscovery/katana)
- [tlsx](https://github.com/projectdiscovery/tlsx)
- [subfinder](https://github.com/projectdiscovery/subfinder)
- [oneforall](https://github.com/shmilylty/OneForAll)

除此之外，还有一些应用：
- [cidr](https://github.com/leveryd-asm/asm/blob/master/templates/argo-workflow-template-asset/level1/cidr/get-cidr.yaml): 根据asn号生成网段、根据ip列表生成最小网段
- [es-client](https://github.com/leveryd-asm/asm/blob/master/templates/argo-workflow-template-asset/level1/logstash/logstash.yaml): 向elaticsearch查询和保存资产信息
- screenshot: 根据url列表截图

"漏洞"相关的应用使用的工具包括：
- [nuclei](https://github.com/projectdiscovery/nuclei)
- 管理后台系统识别

# 怎么使用应用？

应用一般是开发者编写更复杂的工作流模板时调用的，不过你也可以在argo-ui上使用。

# 怎么编写应用？

见 [开发文档](developer/workflow-template/how-to-write)
