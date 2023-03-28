#
# 当想集成的工具没有容器版本怎么办？

比如 [xray](https://github.com/chaitin/xray/)、[fofax](https://github.com/xiecat/fofax) 等都没有镜像版本

有几种选择：
* 自己制作镜像，虽然简单，但是有点麻烦。asm项目用的 [xray镜像](https://github.com/leveryd-asm/tools/tree/main/xray) 就是这么做的
* 在容器中下载二进制文件。asm项目用的 [fofax镜像](https://github.com/leveryd-asm/asm/commit/bc54f40dc6dd5a5331a7124b84a7e14aa3023a2c) 就是这么做的
* 网上看看有没有别人做好的镜像，但安全上第三方的镜像可信度不如官方的高，而且第三方并不一定保证每个版本都有
* 给官方提需求

# 调试工具

在集成工具时，经常需要验证工具参数是否正确。以下是容器版本的工具命令
```
alias httpx='docker run -ti --rm --entrypoint sh projectdiscovery/httpx:v1.2.7'
alias tlsx='docker run -ti --rm --entrypoint sh projectdiscovery/tlsx:v1.0.4'
alias subfinder='docker run -ti --rm --entrypoint sh projectdiscovery/subfinder:v2.5.5'
alias naabu='docker run -ti --rm --entrypoint sh projectdiscovery/naabu:v2.1.1'
alias jq='docker run -ti --rm --entrypoint bash docker.io/imega/jq:1.6'
alias nuclei='docker run -ti --rm --entrypoint sh projectdiscovery/nuclei:v2.8.3'
alias logstash='docker run --entrypoint bash -ti --rm -v /tmp/:/tmp logstash:7.17.3'
```
