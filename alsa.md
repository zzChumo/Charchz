# 全损音质？能用就行
众所周不知，Charchz是无法播放音频的。因此我们又双叒叕要花费亿些时间和精力去配置我们的ALSA和PulseAudio辣！    
    
想要使Charchz播放音频，请执行以下命令：    
    
``` shell
# 安装ALSA相关
pacman -S alsa-utils alsa-plugins
# 安装PulseAudio服务
pacman -S pulseaudio pulseaudio-qt pulseaudio-rtp 
# 因为Charchz没有蓝牙支持所以暂时不用装（？）
pacman -S pulseaudio-bluetooth
# 安装ALSA支持
pacman -S pulseaudio-ALSA
# 安装图形化音量调节工具
pacman -S pavucontrol pavucontrol-qt
# 安装xfce4的音量调节UI（位于顶部Dock栏）
pacman -S xfce4-pulseaudio-plugin
```
    
现在您已经成功安装了两个音频服务！~~您的电脑变垃圾场指日可待！~~现在为了防止音响性能不足真的变成全损音质，我们还需要调整`/usr/share/alsa/alsa.conf`内的`defaults.pcm.dmix.rate`值。该值视音响及声卡性能（最大采样率）而定，一般情况下设定为`44100`即可。    
    
在更改配置以后，在TTY中执行`pulseaudio --start`和`amixer sset Master unmute`，最后通过`startxfce4`启动桌面环境。这时您已经可以通过内置的Google Chrome听歌了。    
    
*注意：您需要在每次启动桌面环境前执行`pulseaudio --start`。您可以将该命令写入`/etc/environment`或创建systemctl文件以实现开机自启。*    
    
[← Swap：从入土到再也不用管](swap.md)
