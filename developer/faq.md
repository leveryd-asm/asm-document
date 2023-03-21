# 当想集成的工具没有容器版本怎么办？

比如 [xray](https://github.com/chaitin/xray/)、[fofax](https://github.com/xiecat/fofax) 等都没有镜像版本

有几种选择：
* 自己制作镜像，虽然简单，但是有点麻烦。asm项目用的 [xray镜像](https://github.com/leveryd-asm/tools/tree/main/xray) 就是这么做的
* 在容器中下载二进制文件。asm项目用的 [fofax镜像](https://github.com/leveryd-asm/asm/commit/bc54f40dc6dd5a5331a7124b84a7e14aa3023a2c) 就是这么做的
* 网上看看有没有别人做好的镜像，但安全上第三方的镜像可信度不如官方的高，而且第三方并不一定保证每个版本都有
* 给官方提需求
