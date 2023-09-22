
<h1 align="center">千机-红队免杀木马自动生成器 By Hyyrent</h1>

## 声明

1. 仅限用于技术研究和获得正式授权的攻防项目，请使用者遵守《中华人民共和国网络安全法》，切勿用于任何非法活动，若将工具做其他用途，由使用者承担全部法律及连带责任，作者及发布者不承担任何法律及连带责任！
2. 为了保证免杀持久性，暂不进行开源，测试尽量通过本地断网环境，避免多次上传沙箱。
3. 主程序可能被部分杀软标记，若报毒为误报，请添加至杀软白名单。
4. 主程序文件hash为`78f9079378049a3c4d5a0789d9ca067c`，自开发程序无后门，不放心可移至虚拟机使用。
5. 使用前先按照文档步骤一步一步来，报错问题先百度自行解决，无营养的issue一律不回，感谢理解！

## 开发目的

在攻防对抗中，免杀木马是使用频率最高的东西，但是制作起来需要耗费大量时间精力，重复性工作会让人产生疲惫和厌烦！
于是我决定开发一款全自动的工具，只需要双击鼠标便可以生成免杀马，因此诞生了这个工具！🤡🤡🤡

我这个人比较喜欢简便，因此设计开发工具时不想添加cmd运行命令和参数，主打一键化生成，更适合脚本小子宝宝的体质！

每次生成对shellcode进行随机混淆加密，生成不同hash和字符串的木马文件，避免被杀软提取特征！
## 环境准备

由于本人比较熟悉go，于是决定用go进行开发，但是说实话在开发过程中感受到了很多局限性，比如依赖库问题，后续开发还是选用其他语言较好

环境准备：安装`go`和`git`，go版本需要`1.20`及以上

https://golang.google.cn/dl/go1.21.0.windows-amd64.msi 下载安装go

![image](https://github.com/Pizz33/Qianji/assets/88339946/4643a8ea-0eb3-47a5-834a-4cf4538e9c04)


 https://git-scm.com/download/win  下载安装git

![image](https://github.com/Pizz33/Qianji/assets/88339946/9a049473-cb1a-4005-9521-4576d745d392)


下载相关garble等相关依赖，命令如下

```
set GOPROXY=https://goproxy.cn,direct
go install mvdan.cc/garble@latest
go mod init 1
go get github.com/darkwyrm/b85
go get github.com/gonutz/ide
```

环境未搭建好，可能会出现以下报错，还有其他报错请自行百度

```
cannot get modified linker: exec: "git": executable file not found in %PATH%
cannot get modified linker: exec: "garble": executable file not found in %PATH%
```

## 使用方法


1、cobaltstrike都有吧，生成`stageless`的`raw`格式文件，把`beacon.bin`和主程序`Qianji_BypassAV.exe`放到同一目录下，别改名字不然会生成失败

![image](https://github.com/Pizz33/Qianji/assets/88339946/26436df3-f8b4-4dc1-89af-1ac3e7f07e45)


2、双击运行，不需要多余的操作，等待木马生成，成功会在当前目录下生成随机六位数的exe木马文件

![image](https://github.com/Pizz33/Qianji/assets/88339946/dc004f1c-2b62-470d-9a32-1fc8f4d360ad)


## 免杀效果

defender

![image](https://github.com/Pizz33/Qianji/assets/88339946/a50fbf65-7aa3-4fcb-b48e-f84ac96e8395)


火绒

![image](https://github.com/Pizz33/Qianji/assets/88339946/aba329c1-1573-45a7-992c-c6072f8a74dc)


360

![image](https://github.com/Pizz33/Qianji/assets/88339946/5b71193c-b2b0-4adb-9883-beac56cae7f3)
