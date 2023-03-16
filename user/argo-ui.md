# argo-ui是什么？

本项目使用[argo-workflow项目](https://argoproj.github.io/argo-workflows)作为任务编排引擎，在argo-ui上你可以使用asm项目内置的工作流模板创建探测资产、漏洞扫描等任务。

> 如果你想了解argo-ui本身的特点，你可以参考[此文档](https://argoproj.github.io/argo-workflows/artifact-visualization/)

比如，如果你想对某个域名做漏洞扫描，就可以选择asm项目内置的`nuclei扫描-保存结果`工作流模板，如下图所示。输入域名后，点击`Submit`按钮，等待扫描完成即可。

![](https://user-images.githubusercontent.com/1846319/225572786-7982b3c6-a9d1-41b7-ba56-e96de62e3ef6.png)

内置还有很多其他的工作流模板，你可以先自行探索，模板功能描述待补充。
