# <!-- {docsify-ignore-all} -->

欢迎使用 <strong>leveryd-asm !</strong> 🎉🎉🎉

# 免责声明

* 禁止用于非法用途，一切违法行为与作者无关。
* 所有 APP 均符合国家相关法律法规，网络安全法等，我方遵守开源协议及 APP 厂商的相关要求。

# leveryd-asm是一款什么软件？

<strong>leveryd-asm</strong>致力于成为一个面向企业的外网攻击面管理产品，企业可以用它来发现自己暴露在互联网的资产、感知这些资产存在的安全漏洞并运营漏洞。

它有以下特点：

<details>
<summary><b>🕸 基于任务编排 </b></summary>
基于<a href="https://argoproj.github.io/argo-workflows/">argo-workflow</a>提供功能丰富、稳定的任务编排能力
</details>

<details>
<summary><b>🔗 基于kubernetes </b></summary>
任务编排引擎基于kubernetes调度工作容器，因此很容易通过水平扩展提升扫描性能；通过kubernetes生态很容易观测、运维应用
</details>

<details>
<summary><b>💻 开箱即用 </b></summary>
内置多条工作流，只需要输入资产信息，就可以完成扫描任务
</details>

<details>
<summary><b>🤖 管理控制台 </b></summary>
向用户提供UI界面管理资产、运营漏洞；对于开发者来说，想要在控制台新增一个模板可以很快，常规的crud操作只需要通过配置选项就能完成模块的前后端开发
</details>

<details>
<summary><b>💡 多实例部署 </b></summary>
同一kubernetes集群可以部署多个asm实例，数据互不影响。所以你可以区分正式环境和线上环境，也可以对不同类型的资产分别部署实例（比如国外资产和国内资产）
</details>

架构如下：
![](https://user-images.githubusercontent.com/1846319/225553724-94c34e58-9dca-4184-afbf-76b8b88b04c7.png)

举几个使用场景的例子：

<table>
  <tr>
      <td width="50%" align="center"><b>提交爬扫任务</b></td>
      <td width="50%" align="center"><b>在控制台上运营报警</b></td>
  </tr>
  <tr>
     <td><img src="https://user-images.githubusercontent.com/1846319/209668967-d2eff688-80b5-4657-9429-51b2c1d06ba8.png"/></td>
     <td><img src="https://user-images.githubusercontent.com/1846319/209669120-0e7ef61b-7c64-47de-8536-3d00cef2c164.png"/></td>
  </tr>
  <tr>
      <td width="50%" align="center"><b>提交POC扫描任务</b></td>
      <td width="50%" align="center"><b>查看任务状态</b></td>
  </tr>
  <tr>
     <td><img  src="https://user-images.githubusercontent.com/1846319/209672294-5e74ab2a-3679-447a-96dc-e5fe595480e5.png"/></td>
     <td><img  src="https://user-images.githubusercontent.com/1846319/209672007-0c3c46be-6245-406c-8935-e4200574abb4.png"/></td>
  </tr>
</table>

# 设计思路
如果你对此产品的实现感兴趣，可以看看以下文章
* [基于任务编排玩一玩漏扫](https://mp.weixin.qq.com/s/CQshF0KsDCPB6AmtOgOBqw)
* [asm项目和爬虫](https://mp.weixin.qq.com/s/fyUJPZ44gKpZF4q4ejA6fQ)
* [asm项目v0.0.2版本总结](https://mp.weixin.qq.com/s/bGmL-XYXLxm3YxQt3sqCzw)
* [asm项目v0.0.3版本总结](https://mp.weixin.qq.com/s/LOqioImlTnXitRq-CW9eXA)
