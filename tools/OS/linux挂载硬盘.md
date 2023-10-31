查看硬盘设备以及它们的分区和挂载点。

```shell
lsblk
```



# 临时手动挂载

挂载名为 `/dev/sda` 的分区到 `/mnt/data` 目录

```shell
sudo mount /dev/sda /mnt/data
```



# 启动时自动挂载

编辑文件 `/etc/fstab` 并追加：

```shell
/dev/sda   /mnt/data   ext4   defaults   0   0
```

`sudo mount -a` 挂载在 `/etc/fstab` 中定义的所有设备和分区。



