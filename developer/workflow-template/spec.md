# <!-- {docsify-ignore-all} -->

# 为什么argo-workflow-template*子目录命名是level1/level2/level3?

为了规范策略的编写：
* level1模板不会调用其他模板，是最基础的"应用"
* level2模板会调用level1模板
* level3模板会调用level2/level1模板

# 目录、文件名、模板名的命名规范
* 模板名需要包含`levelX`字段,这样在argo-ui上会展示顺序

* 资产发现、获取资产 等工作流在 argo-workflow-template-asset 目录
* 漏洞扫描任务流在 argo-workflow-template 目录

* "主动探测资产、被动发现资产"工作流的文件名以`probe-`开头,模板名称以`probe-asset-`开头
* "从asm库中查询资产"工作流的文件名以`get-`开头,模板名称以`get-asset-`开头
