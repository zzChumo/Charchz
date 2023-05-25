# 在您的Charchz上使用AppImage
AppImage依赖于FUSE，但是Charchz的FUSE缺少了几个库，您需要自己安装这些库才能运行AppImage文件。    
    
``` shell
# 安装FUSE
pacman -S fuse2fs fuse2 fuse3 fuse-common
# 安装其他缺失库
pacman -S libxcrypt-compat libxcrypt libscrypt libgcrypt
```
    
[← 中文输入法的安装与配置](fcitx.md) | [使用Google Chrome进行互联网浏览 →](sandbox.md)
