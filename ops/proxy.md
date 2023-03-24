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

# 代理服务数据没有存储到elasticsearch时怎么排查？

步骤一：验证proxify服务

```
[root@192 ~]# kubectl get services -n asm|grep -i proxy
external-proxy-service            ClusterIP   10.233.13.254   <none>        1080/TCP                     63d
xray-proxy-service                NodePort    10.233.11.6     <none>        58088:30088/TCP              63d
[root@192 ~]# curl www.baidu.com -x 'socks5://10.233.13.254:1080'
```

步骤二：验证xray-proxy服务
