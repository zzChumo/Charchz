# 安装

要安装Charchz到您的计算机上，您至少需要一部使用UEFI且硬盘不小于10GB的x86_64设备。您的内存大小应不低于512MB。   
    
首先，您需要在一个已有的操作系统上新建一个大小10GB以上的硬盘分区并格式化为ext4文件系统。对于Windows，可以使用`DiskGenius`免费版和Windows磁盘工具；对于Linux，可以使用`mkfs.ext4`和`GParted`。    
    
接下来，下载Charchz的镜像文件并在**任意Linux发行版**或在**其安装盘**上使用`sudo tar -zxvf charchz-rootfs.tar.gz`将镜像解压至新分区的根目录。不管在解压过程中出现何种类型的报错，您都应该在网络畅通的情况下重新下载镜像并解压。    
    
最后，使用其他系统的Grub**命令行**执行以下命令：

``` shell
set root=(<硬盘名称>,<分区名称>)
insmod linux
linux /boot/vmlinuz-linux root=/dev/<设备名>
initrd initramfs-linux.img
boot
```
    
*在执行这些命令前，您必须保证您的分区没有严重损伤，否则可能会出现因为无法挂载内存盘而导致的Kernel Panic。*    
    
随后，Grub会加载Charchz的内核及内存盘。您需要在TTY中以用户root登录系统。root的默认密码为arch。在成功登陆以后，由于没有设定文件系统默认挂载状态，根目录将自动设为只读。这时，您需要执行`rootrw`临时挂载根目录为读写，使用`lsblk`查看Charchz安装分区的UUID，并在`/etc/fstab`中添加以下内容：    
    
```shell
UUID=<UUID> / ext4 defaults,noatime 0 1
```

最后，请参考[Grub配置教程](grub.md)以安装Grub到您的硬盘上。  
   
现在，Charchz已经成功安装到了您的电脑上。您可以使用`passwd`来修改您的root用户密码。同时，Charchz还内置了一个名为`arch`的sudo用户，您可以使用它来完成后续的操作。     

如果您不希望使用物理环境进行配置，您也可以考虑在解压Charchz后使用Chroot执行相同操作。  
    
[← TODO](todo.md) | [系统配置指南 →](system.md)
