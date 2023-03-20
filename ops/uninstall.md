# 如何卸载本项目
```
helm -n asm template ./ | kubectl delete -n asm -f -
```

如果你不想保留数据，就还需要手动删除pvc、pv资源

```
kubectl delete pvc -n asm --all   # 删除pvc
kubectl delete pv -n asm --all    # 删除pv
```
