# Ubuntu 安装JDK 8 & JDK 11

参考文档：https://www.linuxbabe.com/ubuntu/install-oracle-java-8-openjdk-11-ubuntu-18-04-18-10

主要按照上述文档翻译一下主要内容：

Java 11 发布于2018年5月份，这是自从Oracle更改其发布策略以后的第一个长期支持版本。

**Java的发布模式简介**

之前，Oracle每两年发布一个java的主版本，每6个月发布一个小版本。但是 Java 9 发布用了3年，因为jigsaw？有些人，比如一些公司，比较喜欢这个模式，因为产品比较稳定。其他人，比如开发者，比较喜欢新东西，感觉这个太慢了。

自 Java 9以后，Oracle每6个月发布一个主版本，每3年会有一个LTS版本（long time support)，会持续支持8年，兼顾开发者和企业用户。Java 11是第一个长期支持版本。下一个长期支持版本是 Java 17。Java 8 到2025年就停止支持了。非LTS版本在下一个版本出来以后就不会再更新了。因此 Java 9 和 Java 10 已经停止更新。

**OpenJDK vs Oracle JDK**

自从Java 9 以后，Oracle 开始提供其自己的OpenJDK。并将一些闭源的特性，比如 Java flight recorder和 Java mission control，推送到了OpenJDK。从 Java 11 开始，Oracle Open JDK 和 Oracle JDK在功能上已经保持一致，相互兼容。两者主要区别是表面的，包管理？还有授权上。如果你要商业支持，那么请用Oracle JDK，其发布授权协议为OTN（Oracle Technology Network）。

**安装Java 8**

Java 8 不再使用BCL(Binary Code License)，从2019年4月16日起，Oracle JDK 8 使用OTN授权。因此需要注册Oracle账号来下载 JDK 8。`https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html`

等下载后，可以将其解压到/usr/lib/jvm/下面（该路径默认安装路径）。

`sudo tar xvf jdk-8u221-linux-x64.tar.gz --directory /usr/lib/jvm/`

检查版本：

`/usr/lib/jvm/jdk1.8.0_221/bin/java -version`

输出如下：

`java version "1.8.0_221" Java(TM) SE Runtime Environment (build 1.8.0_221-b11)
Java HotSpot(TM) 64-Bit Server VM (build 25.221-b11, mixed mode)`

**安装Java 11**

因为Oracle 的OpenJDK 11和其Oracle JDK 11功能相同，因此如果你不需要Oracle 的商业服务支持，强烈建议你使用OpenJDK，因为其包管理集成和更新都比较方便。

使用如下命令即可在Ubuntu 18.04，19.04，20.04上安装OpenJDK。

`sudo apt install openjdk-11-jdk`

同时会安装 `openjdk-11-jre` 包，其包含了java的运行时包，完了可以用下面的命令检查版本：

`java -version`

输出如下：

`openjdk 11.0.4 2019-07-16 OpenJDK Runtime Environment (build 11.0.4+11-post-Ubuntu-1ubuntu219.04)
OpenJDK 64-Bit Server VM (build 11.0.4+11-post-Ubuntu-1ubuntu219.04, mixed mode, sharing)`

**设置默认版本SDK**

第一步：将JDK 8 放在选择系统下面：

`sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk1.8.0_221/bin/java 1
sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk1.8.0_221/bin/javac 1`

使用如下命令选择默认JDK版本

`sudo update-alternatives --config java`

`sudo update-alternatives --config javac`


