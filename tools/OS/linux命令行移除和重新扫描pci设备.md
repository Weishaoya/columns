```shell
$ lspci | grep NVIDIA
02:00.0 3D controller: NVIDIA Corporation Device 2235 (rev a1)
03:00.0 3D controller: NVIDIA Corporation Device 2235 (rev a1)
82:00.0 VGA compatible controller: NVIDIA Corporation GP104 [GeForce GTX 1080] (rev a1)
82:00.1 Audio device: NVIDIA Corporation GP104 High Definition Audio Controller (rev a1)
83:00.0 3D controller: NVIDIA Corporation Device 2235 (rev a1)
```



```shell
$ sudo su
# echo 1 > /sys/bus/pci/devices/0000:82:00.0/remove
# echo 1 > /sys/bus/pci/devices/0000:82:00.1/remove
```

如果要加上设备，只需重新扫描

```shell
# echo 1 > /sys/bus/pci/rescan
```

```shell
02:00.0 3D controller: NVIDIA Corporation Device 2235 (rev a1)
03:00.0 3D controller: NVIDIA Corporation Device 2235 (rev a1)
83:00.0 3D controller: NVIDIA Corporation Device 2235 (rev a1)
```

