# 如何卸载本项目
```
helm -n asm template ./ | kubectl delete -n asm -f -
```
