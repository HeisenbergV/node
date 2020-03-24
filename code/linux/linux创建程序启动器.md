### /usr/share/applications/ 目录下存在着所有应用的启动程序,后缀 .desktop

Desktop Entry

### 以eclipse为例
1. 在此目录创建eclipse.desktop
2. 输入:

```
 [Desktop Entry]
Name=Eclipse
Type=Application
Exec=/home/zuo/下载/eclipse-installer/eclipse-inst --启动程序所在目录/
Terminal=false
Icon=/home/zuo/下载/eclipse-installer/icon.xpm --程序图标目录
Comment=Integrated Development Environment
NoDisplay=false
Categories=Development;IDE
Name[en]=eclipse.desktop
```

https://www.ibm.com/developerworks/cn/linux/l-cn-dtef/