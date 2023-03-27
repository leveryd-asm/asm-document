asm实例运行中如果有一些异常数据，就说明可能哪个环节有问题需要排查。

# first_create_time 为空的记录
* 怎么监控？

  kibana新建dashboard监控

* 发现有空的记录时怎么处理？

  补全 first_create_time 为空的数据

  ```
  POST /subdomain/_update_by_query
  {
    "query": {
      "bool": {
        "must_not": {
          "exists": {
            "field": "first_create_time"
          }
        }
      }
    },
    "script": {
      "source": """
        ctx._source.first_create_time = ctx._source["@timestamp"]
      """
    }
  }
  ```
