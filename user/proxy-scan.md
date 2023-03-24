# 验证代理服务是否可用
步骤一：验证代理是否可用

```
➜  ~ curl www.apple.com -x console.com:30088 -I
HTTP/1.1 301 Moved Permanently
...
Location: https://www.apple.com/
```

步骤二：验证请求是否成功存储

查看proxify索引文档数量是否增加
