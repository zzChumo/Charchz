# GRUB的安装与命令行下的手动引导
Grub是一个Linux下的系统引导工具，您可以使用它来引导您的Charchz系统。    
    
在第一次安装时Charchz使用其他系统/安装盘的Grub进行引导。而现在，您将让您的Charchz拥有一个属于自己的Grub。    
    
首先，您需要在系统中挂载您的EFI分区到指定目录上，然后执行`grub-install /dev/<硬盘名称> --target=x86_64-efi --efi-directory=<EFI挂载目录>`来安装Grub到您的硬盘上。如果您使用传统的BIOS启动方式则不需要挂载EFI分区，直接执行`grub-install /dev/<硬盘名称> --target=i386-pc`即可。    
    
接下来，您需要创建`/boot/grub/grub.conf`以建立Grub的启动菜单。您需要执行`grub-mkconfig -o /boot/grub/grub.cfg`以创建grub.cfg。  
    
如果您~~非常的懒以至于懒得复制粘贴~~想要保证系统的简洁和最小化或在公共场所装13，则可以在Grub命令行中通过以下命令来手动引导内核：    
    
``` shell
set root=(<硬盘名称>,<分区名称>)
insmod linux
# 因为命令需要手动输入 所以我们可以不输入UUID 你可以通过硬盘在主板上的插槽位置来确定硬盘名称 根据Grub提供的分区名称来确定分区编号
linux /boot/vmlinuz-linux root=/dev/<硬盘名称+分区编号>
initrd /boot/initramfs-linux.img
boot
```
    
至此，通过重启来尝试你新安装的Grub吧。    
    
[← 系统维护指南](system.md) | [无线网卡的使用 →](wl.md)
