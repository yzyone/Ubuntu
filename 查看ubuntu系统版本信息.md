# 查看ubuntu系统版本信息 #

以下内容转载自：百度知道。

方法一：cat /etc/issue

返回结果：

	Ubuntu 8.04.1 \n \l

方法二：cat /proc/version

返回结果：

	Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Aug 25 17:32:09 UTC 2008

方法三：uname -a

返回结果：

	Linux wwt-laptop 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

方法四：lsb_release -a

返回结果：

```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 8.04.1
Release:    8.04
Codename:    hardy
```

方法五：cat /etc/lsb-release

返回结果：

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
```

参考链接：https://blog.csdn.net/it1988888/article/details/8039322