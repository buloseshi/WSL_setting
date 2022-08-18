# 一、图形界面桌面
1、windows安装vcxsrv，安装包如下[vcxsrv-64.1.20.14.0.installer.zip](https://moweai.yuque.com/attachments/yuque/0/2022/zip/22860708/1660270509782-8069f3e5-1ffd-48e8-a363-0af1772ebe21.zip?_lake_card=%7B%22src%22%3A%22https%3A%2F%2Fmoweai.yuque.com%2Fattachments%2Fyuque%2F0%2F2022%2Fzip%2F22860708%2F1660270509782-8069f3e5-1ffd-48e8-a363-0af1772ebe21.zip%22%2C%22name%22%3A%22vcxsrv-64.1.20.14.0.installer.zip%22%2C%22size%22%3A42861938%2C%22type%22%3A%22application%2Fx-zip-compressed%22%2C%22ext%22%3A%22zip%22%2C%22source%22%3A%22%22%2C%22status%22%3A%22done%22%2C%22mode%22%3A%22title%22%2C%22download%22%3Atrue%2C%22taskId%22%3A%22ua9fd84d9-1ec2-43d7-9f0c-e492bb9092f%22%2C%22taskType%22%3A%22upload%22%2C%22__spacing%22%3A%22both%22%2C%22id%22%3A%22efU5B%22%2C%22margin%22%3A%7B%22top%22%3Atrue%2C%22bottom%22%3Atrue%7D%2C%22card%22%3A%22file%22%7D)，一路默认设置即可。安装完成后打开，前两个默认设置即可，在Extra setting界面选择Disable access contorl，禁用访问控制。
![image.png](https://cdn.nlark.com/yuque/0/2022/png/22860708/1660270554531-26b33654-c848-4178-8b3b-95162c3a7fe3.png#clientId=u28db9aa0-65bc-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=365&id=L2Lxu&margin=%5Bobject%20Object%5D&name=image.png&originHeight=402&originWidth=504&originalType=binary&ratio=1&rotation=0&showTitle=false&size=42607&status=done&style=none&taskId=u35fcc7a8-135c-4fe4-a0ad-d14d4469cdb&title=&width=458.18180825099495)![image.png](https://cdn.nlark.com/yuque/0/2022/png/22860708/1660270617496-eff8a654-ad72-49e8-83df-8116ec89e511.png#clientId=u28db9aa0-65bc-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=374&id=u0c343460&margin=%5Bobject%20Object%5D&name=image.png&originHeight=411&originWidth=502&originalType=binary&ratio=1&rotation=0&showTitle=false&size=14979&status=done&style=none&taskId=u0fe34d52-b327-48d1-a880-166a9a6807b&title=&width=456.36362647222114)![image.png](https://cdn.nlark.com/yuque/0/2022/png/22860708/1660271994237-6463d977-2d9c-433f-872b-b2e158dde5e7.png#clientId=uc62a1dfa-5d43-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=368&id=ua7eaf991&margin=%5Bobject%20Object%5D&name=image.png&originHeight=405&originWidth=501&originalType=binary&ratio=1&rotation=0&showTitle=false&size=8552&status=done&style=none&taskId=uceb271e1-beee-49ce-966e-27be8be38c5&title=&width=455.45453558283424)
完成后在Finish configuration界面可以选择保存配置，生成一个快捷方式，下次直接打开快捷方式即可。
2、打开WSL，使用如下命令安装xfce，以及显示管理器gdm3

1. sudo apt-get install xfce4-terminal
1. sudo apt-get install xfce4
1. sudo apt-get install gdm3

3、WSL终端输入
export DISPLAY=`cat /etc/resolv.conf | grep nameserver | awk '{print $2}'`:0
可自行修改使用vim修改~/.bashrc，在最后一行添加以上命令，避免二次打开重复输入，不改需要每次重启wsl都输入
4、WSL终端输入以下命令即可
sudo startxfce4
5、其他wsl软件安装可参考如下：
图片操作：sudo apt install gimp -y
文件管理器：sudo apt install nautilus -y
X11应用（各种软件包的集合，比如复制剪切，计算器，日历等）：sudo apt install nautilus -y
2、启动ubuntu-desktop桌面（两个桌面功能相同）
打开win端xLaunch，窗口选择
 sudo apt update
 sudo apt install ubuntu-desktop
 sudo apt install gnome-session
 sudo DISPLAY=`cat /etc/resolv.conf | grep nameserver | awk '{print $2}'`:0 XDG_SESSION_TYPE=x11 gnome-session
# 二，WSL2访问USB设备
本方法需要 Windows Build 19041 及以后版本，且仅限 WSL 2 使用，本办法能够通过 Windows 侧安装的 USBIP 来将 USB 数据包转发至 Linux 侧的 USBIP，从而让 WSL 2 支持 USB 设备。默认情况下，WSL 2 的 Linux 内核并不支持 USB，本文将介绍如何向 WSL 2 的 Linux 内核中添加 USB 功能，以及如何用 USBIP 将 USB 设备连接至 Linux 上。（推荐安装ubuntu-preview发行版，向下兼容，内核支持更全面）
win端，安装[usbipd-win_2.3.0.zip](https://moweai.yuque.com/attachments/yuque/0/2022/zip/22860708/1660801360604-d3a65c28-3dde-448b-86d4-dfeb8580a629.zip?_lake_card=%7B%22src%22%3A%22https%3A%2F%2Fmoweai.yuque.com%2Fattachments%2Fyuque%2F0%2F2022%2Fzip%2F22860708%2F1660801360604-d3a65c28-3dde-448b-86d4-dfeb8580a629.zip%22%2C%22name%22%3A%22usbipd-win_2.3.0.zip%22%2C%22size%22%3A10085287%2C%22type%22%3A%22application%2Fx-zip-compressed%22%2C%22ext%22%3A%22zip%22%2C%22source%22%3A%22%22%2C%22status%22%3A%22done%22%2C%22download%22%3Atrue%2C%22taskId%22%3A%22u203ec105-46ad-4704-aaa6-d1bfdc55605%22%2C%22taskType%22%3A%22upload%22%2C%22__spacing%22%3A%22both%22%2C%22id%22%3A%22uf3289f27%22%2C%22margin%22%3A%7B%22top%22%3Atrue%2C%22bottom%22%3Atrue%7D%2C%22card%22%3A%22file%22%7D)
Ubuntu端，执行
sudo apt install linux-tools-5.4.0-77-generic hwdata
sudo update-alternatives --install /usr/local/bin/usbip usbip /usr/lib/linux-tools/5.4.0-77-generic/usbip 20
wIN端管理员打开powershell，输入usbipd wsl list，查看目前连接的USB设备，运行usbipd wsl attach --busid <busid>，将USB设备附加到Linux环境。
如Powershell端显示该发行版不支持usb，则需要更新WSL内核，，参考该文档查看WSL内核说明。
升级内核的简易方法是，windown软件商店安装，Windows Subsystem for Linux Preview，自动将win当前默认发行版升级到最新内核以支持USB访问能力。如果不想升级内核，则需要重新编译内核，添加USB支持，参考。推荐直接安装软件，简单迅速且不会对当前发行版造成任何影响。
安装完成后，重启打开linux发行版，输入uname -r，显示5.15.57.1-microsoft-standard-WSL2, 或更高版本即可。
打开WIN端powershell，usbipd wsl list，usbipd wsl attach --busid <busid>, 没有报错，显示成功挂载，linux端输入，lsusb，列出目前连接的USB设备，以进一步操作。
