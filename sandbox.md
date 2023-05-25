# 使用Google Chrome进行互联网浏览
Charchz为您内置了一个Google Chrome。但由于Google的安全政策，您无法使用root启动带有sandbox的Chrome，且Chromium和Electron等应用也采用了相同的政策。因此，您需要以不带沙箱的方式启动它们。

首先，你需要编辑它们的快捷方式，例如在`Exec`中的命令后加入`--no-sandbox`参数。

但是并不是所有的应用都采用这种方式来启动，比如`zzchat-elec`，它采用了一个Shell脚本来启动内部的Electron。因此，单独编辑快捷方式是没有用的。你需要更改它位于`/usr/bin`的启动脚本，并在脚本的第二行末尾加入`--no-sandbox`参数。    
    
[← 在您的Charchz上使用AppImage](app.md) | [Swap：从入土到再也不用管 →](swap.md)
