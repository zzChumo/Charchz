# Swap：从入土到再也不用管
内存条不够用？试试大名鼎鼎的Swap！    
    
要添加Swap，你首先需要通过`pacman -S gparted`获取`GParted`。这是一个非常好用的磁盘管理工具，比fdisk更加友好，也更加安全。    
    
然后打开您刚刚安装的GParted，新建一个硬盘分区并选择文件系统为`limux-swap`，之后提交修改。    
    
*注意：Swap会消耗您的硬盘寿命！请创建不超过4GiB的Swap分区！*     
    
最后，在`/etc/fstab`中添加如下内容：    
    
``` shell
# Swap的UUID可以通过blkid获取
UUID=<UUID> none swap defaults 0 0
```
    
如果您想要立即启用您的Swap，您只需要执行`swapon /dev/<分区名称>`即可。     
    
[← 使用Google Chrome进行互联网浏览](sandbox.md)
