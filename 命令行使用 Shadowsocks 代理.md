# 命令行使用 Shadowsocks 代理 #

在这里顺便分享一下如何在命令行挂上 Shadowsocks 代理：

```
sudo apt-get install python-pip
sudo pip install shadowsocks
sudo apt-get install proxychains

wget https://download.libsodium.org/libsodium/releases/LATEST.tar.gz
tar zxf LATEST.tar.gz && cd libsodium*
./configure && make && make install
# 修复关联
echo /usr/local/lib > /etc/ld.so.conf.d/usr_local_lib.conf && ldconfig
```

/etc/shadowsocks.json 配置内容：

```
{
"server":"server-ip",
"server_port":8000,
"local_address": "127.0.0.1",
"local_port":1080,
"password":"your-password",
"timeout":600,
"method":"aes-256-cfb"
}
```

~/.proxychains/proxychains.conf 配置内容：

```
strict_chain
proxy_dns
remote_dns_subnet 224
tcp_read_time_out 15000
tcp_connect_time_out 8000
localnet 127.0.0.0/255.0.0.0
quiet_mode

[ProxyList]
socks5  127.0.0.1 1080
```

执行下述命令之后，命令行程序就会使用 Shadowsocks 代理了：

```
sudo sslocal -c /etc/shadowsocks.json -d start
proxychains bash
```