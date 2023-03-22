```
document_id => ip_host_port"
```

```
{
  "mappings": {
    "_doc": {
      "properties": {
        "first_create_time": {
          "type": "date"
        },
        "host": {
          "type": "text",
          "fields": {
            "keyword": {
              "type": "keyword",
              "ignore_above": 256
            }
          }
        },
        "ip": {
          "type": "text",
          "fields": {
            "keyword": {
              "type": "keyword",
              "ignore_above": 256
            }
          }
        },
        "link": {
          "type": "text",
          "fields": {
            "keyword": {
              "type": "keyword",
              "ignore_above": 256
            }
          }
        },
        "port": {
          "type": "long"
        },
        "timestamp": {
          "type": "date"
        }
      }
    }
  }
}
```
