# Ubuntu20.04 Desktop安装tigervnc-server #

**一、准备**

由于使用的是desktop版，默认为gnome桌面

 

**二、安装TigerVNC服务器**

TigerVNC，是一个主动维护的高性能VNC服务器

	sudo apt install tigervnc-standalone-server
 

**三、修改配置文件**

如果home目录下没有.vnc目录，新建目录

	touch $HOME/.vnc/xstartup

修改xstartup， vim .vnc/xstartup， 修改为以下内容：

```
#!/bin/sh

unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
/etc/X11/xinit/xinitrc
# Assume either Gnome or KDE will be started by default when installed
# We want to kill the session automatically in this case when user logs out. In case you modify
# /etc/X11/xinit/Xclients or ~/.Xclients yourself to achieve a different result, then you should
# be responsible to modify below code to avoid that your session will be automatically killed
if [ -e /usr/bin/gnome-session -o -e /usr/bin/startkde ]; then
    vncserver -kill $DISPLAY
fi
```

修改xstartup权限

	chmod u+x xstartup
 

四、创建vnc端口

- 一定要加上 -localhost no， 否则只能本地连接，不能实现远程连接，那么vnc就毫无意义
- 关闭防火墙，否则可能无法连接

	vncserver :1  -geometry 1920x1000  -depth 24 -localhost no

参考链接：https://www.cnblogs.com/linagcheng/p/15745041.html