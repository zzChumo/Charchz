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
    
随后，Grub会加载Charchz的内核及内存盘。您需要在TTY中以用户root登录系统。root的默认密码为arch。

执行tmoe命令，在nmtui中连接你的无线网络并退出tmoe。之后，执行pacman -Syyu && pacman -S grub以安装Grub，最后通过正常流程将Grub添加到自己的硬盘中即可。
