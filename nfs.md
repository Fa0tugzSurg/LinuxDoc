# Network File System

## 服务器端配置

* 安装nfs-kernel-server

```
$sudo apt-get install nfs-kernel-server -y
```

* 编辑配置文件exports

```
$sudo vi /etc/exports
添加以下内容:
/home/huangfu/nfs 192.168.1.235(rw,sync,no_root_squash) //目录路径根据自己的路径设置,ip为客户端IP，写*也可以，任何IP都可以
```

* 重启nfs 服务器


```
$/etc/init.d/nfs-kernel-server restart
```

* 查看配置状态

```
$showmount -e
```

## 客户端配置

* 直接挂载nfs

```
$sudo mount -t nfs -o nolock 192.168.0.106:/home/huangfu/nfs /mnt/   //ip地址为nfs服务器的ip，路径为服务器端设置的路径
```

## 常见错误


