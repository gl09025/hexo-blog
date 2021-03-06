---
title: 安装shasowsocks
date: 2017-02-19 16:43:03
updated: 2018-01-09 02:19:04
tags: 
  - SS
categories:
  - 科学上网
thumbnail:
---
### ubuntu
```bash
sudo apt-get install python-pip
sudo pip install shadowsocks
```

```bash
sudo vi /etc/shadowsocks.json
```

```bash
{
    "server":"0.0.0.0",    
    "server_port":8080,    // ss端口，自己定义，下面会用到
    "local_address":"127.0.0.1",
    "local_port":1080,
    "password":"123",    //ss密码，下面会用到
    "timeout":300,
    "method":"aes-256-cfb",
    "fast_open":false
}
```

```bash
sudo ssserver -c /etc/shadowsocks.json -d start
```

```bash
sudo ssserver -c /etc/shadowsocks.json -d restart

sudo ssserver -c /etc/shadowsocks.json -d stop
```

### 开机启动

```bash
sudo vi /etc/init.d/shadowsocks
```

```bash
#!/bin/sh
### BEGIN INIT INFO
# Provides:          shadowsocks
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: start shadowsocks 
# Description:       start shadowsocks
### END INIT INFO

start(){
    ssserver -c /etc/shadowsocks.json -d start
}

stop(){
    ssserver -c /etc/shadowsocks.json -d stop
}

case "$1" in
start)
    start
    ;;
stop)
    stop
    ;;
reload)
     stop
     start
     ;;
*)
    echo "Usage: $0 {start|reload|stop}"
    exit 1
    ;;
esac
```

注意：这里命令是以root权限运行，如果不想以root权限运行可以用将命令改为sudo -u {user} {command}
增加这个文件的可执行权限
```bash
sudo chmod +x /etc/init.d/shadowsocks
```
在 rc.d 中新增
```bash
sudo update-rc.d shadowsocks defaults
```

好了，搞定，可以在shell中直接运行sudo service shadowsocks {start|reload|stop}来控制了！