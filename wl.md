# 无线网卡的使用
如果您对无线局域网重度依赖的话，那么您一定希望在Charchz上使用无线网卡。但是很不幸的是，我们在构建系统的时候~~忘记了这玩意儿~~希望能够提升用户的动手能力和问题排查能力，所以没有内置无线网卡驱动。因此，您需要根据以下教程手动完成无线网卡的配置。    
    
首先，确定您正在使用什么类型的网卡。如果您正在使用USB无线网卡，安装`usbutils`；如果您正在使用电脑自带的网卡，则安装`pciutils`。
    
``` shell
# 如果您没有互联网连接的话，您可以将您身边的Android设备插入您的电脑，并在系统设置中打开“USB网络传输”（但是HarmonyOS阉割了这一选项）
# 如果您刚刚才完成系统安装，那么请务必先执行pacman -Syyu

# 如果使用USB
pacman -S usbutils
# 如果使用PCI（插在电脑内部）
pacman -S pciutils
```
    
然后安装无线网卡驱动并重启：    
    
``` shell
pacman -S broadband-wl
reboot
```
    
最后，您可以执行`tmoe`，在`Tools→Secret Garden→network→enable device`中连接您的无线局域网。    
    
如果您偏好我们为您准备的xfce4桌面环境，则可以再安装以下X11支持：    
    
``` shell
pacman -S nm-connection-editor iwgtk
```
    
[← Grub的安装与命令行下的手动引导](grub.md) | [通过xfce4进行高效的生产 →](xfce.md)
