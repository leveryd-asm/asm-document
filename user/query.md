#

目前所有的资产数据和漏洞数据都是存放在mysql和elasticsearch中，在工作流中有三种方式查询数据：
* 输入sql，直接从db中获取数据。参考`level3-crawl-scan`工作流中的`获取扫描优先级高的兄弟域名-获取子域名-katana爬虫-xray扫描-保存结果`
* 从console-api中获取数据。参考`level3-nuclei`工作流中的`从API获取兄弟域名-获取子域名-nuclei扫描-保存结果`
* 从elasticsearch中获取数据。参考`level2-es-nuclei`工作流中的`es查询webservice获取url列表-nuclei扫描-保存结果`

下面向你介绍在工作流使用时可能用到的查询条件

# 从elasticsearch查询

web-service索引
```
domain.keyword:*.apple.com    域名以apple.com结尾
domain.keyword:???.apple.com  ?表示任意单个字符
org:apple                     apple组织
port:>=8000 AND port:<=9000   port在8000-9000之间，注意AND不能小写，也不能写成&&
first_create_time:[2023-03-23 TO 2023-03-25]          23号到25号创建
last_update_time:[2023-03-23 TO 2023-03-25]           23号到25号有过更新
status-code:200 AND content-type:"html" AND words:>10 提供web服务的网站
```

> 语法参考 [elasticsearch文档](https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-query-string-query.html)

# 从console-api查询

<img width="330" alt="image" src="https://user-images.githubusercontent.com/1846319/226902737-78407066-d1cc-4185-a32e-10ef7be4f0d1.png">

响应中所有的字段都可以作为api的查询条件

# 从db查询

```
select rootdomain from brotherdomain where id>=17 limit 30  从兄弟域名中获取部分域名扫描
```
