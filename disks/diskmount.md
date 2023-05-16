# 磁盘挂载

在最开始接触linux磁盘时， 网上的各种教程令我头疼，经过我的一番探索， 我总结了我在磁盘挂载的一些经验

## 1. 查看磁盘的相关信息

### 使用fdisk命令查看磁盘信息

```bash
sudo fdisk -l
```

![screenshot](../asserts/proxy/Screenshot%20from%202023-04-27%2016-55-52.png)

### 也可以使用blkid命令查看磁盘信息

```bash
sudo blkid -f
```

![screenshot](../asserts/proxy/Screenshot%20from%202023-04-27%2017-04-47.png)

这将会显示所有的磁盘信息，包括磁盘的uuid，磁盘的类型，磁盘的挂载点等等

## 2. 挂载磁盘

### 开机启动挂载ntfs磁盘

```bash
# 向 /etc/fstab 添加一行
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# this is a example 
UUID=A002C4C002C49CA2 /mnt/SharePart               ntfs    errors=remount-ro 0       0

# 其中dump指定是否备份，pass指定是否开机自检， UUID即是上一节中可以看到的磁盘分区的UUID
```

### 当然也可以使用mount命令挂载磁盘

```bash
# mount -t <type> <device> <mount point>
# this is a example
sudo mount -t ntfs /dev/sda3 /mnt/SharePart
```
