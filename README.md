
<h1 align="center">千机-红队免杀木马自动生成器 By Hyyrent</h1>

## 更新说明

自开发程序无后门，不放心可移至虚拟机使用，历史程序hash为：
`78f9079378049a3c4d5a0789d9ca067c`
`c2ce6206d2e86a408dd7a2a35d8ecf60`
`0d16c02956f07863b7ef473e32204e6b`
`f9dfef61948a07a2c81653370b21be35`

时间 2023/11/15 趁文章上架更新一波基础版，修复之前报毒问题，目前测试360、火绒、def都可以过，但可能过段时间又被加特征了，后续看情况随缘更新吧哈哈，祝各位师傅玩的开心！🤡🤡🤡

⭐⭐⭐运行前先运行`安装依赖.bat`，接着安装文档把环境先搭建好，运行不起来没反应大概率是没安装gcc！⭐⭐⭐

![image](https://github.com/Pizz33/Qianji/assets/88339946/88e6fbe5-63bb-4ed9-9b81-21e548798eab)

![image](https://github.com/Pizz33/Qianji/assets/88339946/f38462a3-73fc-488e-aee8-f020c33b5589)

输出免杀马文件存放在output文件夹里

![image](https://github.com/Pizz33/Qianji/assets/88339946/863b2dbd-122b-4543-af3e-990ee238357d)


## 声明

1. 仅限用于技术研究和获得正式授权的攻防项目，请使用者遵守《中华人民共和国网络安全法》，切勿用于任何非法活动，若将工具做其他用途，由使用者承担全部法律及连带责任，作者及发布者不承担任何法律及连带责任！
2. 为了保证免杀持久性，暂不进行开源，测试尽量通过本地断网环境，避免多次上传沙箱。
3. 主程序可能被部分杀软标记，若报毒为误报，请添加至杀软白名单。
4. 使用前先按照文档步骤一步一步来，报错问题先百度自行解决，无营养的issue一律不回，感谢理解！

## 开发目的

在攻防对抗中，免杀木马是使用频率最高的东西，但是制作起来需要耗费大量时间精力，重复性工作会让人产生疲惫和厌烦！
为了方便各位师傅在攻防比赛中快速生成免杀木马，取得更好的成绩，于是我决定开发一款全自动工具，只需要双击鼠标便可以生成免杀马！🤡🤡🤡 

我这个人比较喜欢简便，因此设计开发工具时不想添加cmd运行命令和参数，主打一键化生成，更适合脚本小子宝宝的体质！

每次生成对shellcode进行随机混淆加密，生成不同hash和字符串的木马文件，避免被杀软提取特征！⭐⭐⭐

## 环境准备

由于本人比较熟悉go，于是决定用go进行开发，但是说实话在开发过程中感受到了很多局限性，比如依赖库问题，后续开发还是选用其他语言较好

环境准备：安装`go`和`git`，go版本需要`1.20`及以上

https://golang.google.cn/dl/go1.21.0.windows-amd64.msi 下载安装go

![image](https://github.com/Pizz33/Qianji/assets/88339946/4643a8ea-0eb3-47a5-834a-4cf4538e9c04)

https://jmeubank.github.io/tdm-gcc/articles/2021-05/10.3.0-release 下载安装 gcc

![image](https://github.com/Pizz33/Qianji/assets/88339946/08e88ebd-4742-4778-954a-afce7c6d6ec9)

 https://git-scm.com/download/win  下载安装git

![image](https://github.com/Pizz33/Qianji/assets/88339946/9a049473-cb1a-4005-9521-4576d745d392)


下载相关garble等相关依赖，命令如下，也可以直接运行压缩包里的`安装依赖.bat`

```
set GOPROXY=https://goproxy.cn,direct
go install mvdan.cc/garble@latest
go mod init 1
go get github.com/darkwyrm/b85
```

环境未搭建好，可能会出现以下报错，添加至环境变量即可，还有其他报错请自行百度

```
cannot get modified linker: exec: "gcc": executable file not found in %PATH%
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
