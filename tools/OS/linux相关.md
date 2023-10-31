[toc]



# 常用命令

## 防止服务器任务随终端退出而中断

```
ctrl+z  # 暂停当前任务
jobs  # 查看当前终端任务
disown -h %1  # 使任务 1 不受终端影响
bg %1  # 后台运行任务 1
```

## kill

# 用户

创建用户并将其添加到 sudo 组

```
# adduser username
# usermod -aG sudo username
```



# 主机名

修改并查看主机名

```
# hostnamectl set-hostname ubuntu
# hostnamectl
   Static hostname: ubuntu
         Icon name: computer-vm
           Chassis: vm
        Machine ID: 20210922095802902033212080128428
           Boot ID: b3b00e87b8b0437ab3b7c64c864f7049
    Virtualization: kvm
  Operating System: Ubuntu 20.04.3 LTS
            Kernel: Linux 5.4.0-86-generic
      Architecture: x86-64
# reboot  # 重启
```





# ssh

```
$ ssh
usage: ssh [-46AaCfGgKkMNnqsTtVvXxYy] [-B bind_interface]
           [-b bind_address] [-c cipher_spec] [-D [bind_address:]port]
           [-E log_file] [-e escape_char] [-F configfile] [-I pkcs11]
           [-i identity_file] [-J [user@]host[:port]] [-L address]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-Q query_option] [-R address] [-S ctl_path] [-W host:port]
           [-w local_tun[:remote_tun]] destination [command]
```



ssh 登录远程服务器的 zb 用户

```
$ ssh zb@101.132.121.87
```



配置免密登录

```
$ vim ~/.ssh/config
$ cat ~/.ssh/config
Host ubuntu
        HostName 101.132.121.87
        User zb
        IdentityFile ~/.ssh/id_rsa
$ ssh-copy-id zb@101.132.121.87
$ ssh ubuntu
```



# 环境变量

查看环境变量

```
$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
```



# 安装

安装 flex 与 bison

```
# apt install flex bison
# flex --version
flex 2.6.4
# bison --version
bison (GNU Bison) 3.5.1
```





# 使用 CLion 远程连接服务器

1. 配置 ssh 连接服务器并配置映射：在 `Settings - Build, Execution, Deployment - Deployment` ，添加 `SFTP` 配置，在 `connection` 处配置 `ssh` 连接，在 `Mappings` 处配置本地文件夹与服务器文件夹之间的映射。

2. 右键 `Deployment` `upload to xxx` 上传文件及文件夹。

3. 启用 `Tools - Deployment - Automatic Upload(always)` 保持同步。

4. Ubuntu 安装 `cmake` 跨平台编译控制工具与 `gdb` 调试工具。

   ```
   sudo apt install cmake gdb
   ```

5. 进入 `Settings - Build, Execution, Deployment` 在 `Toolchain` 中添加远程主机工具链，在 `CMake` 中选择远程主机工具链，勾选 `Automatically reload CMake project on editing` 。

6. 在 `Run/Debug Configuration` 中创建 `CMake Application` 。

7. build and run Application, 此时应该运行成功。并且可以成功 debug 。

参考文献：

[使用Clion优雅的完全远程自动同步和远程调试c++](https://cloud.tencent.com/developer/article/1406250) 

[搭建CLion远程调试开发环境](https://zhuanlan.zhihu.com/p/344677503) 

[clion远程调试输出乱码](https://blog.csdn.net/chengkaibing521521/article/details/105905665/) 


# GPU

## 查看 gpu 使用情况

```shell
nvidia-smi
```

## 运行时指定 gpu

```shell
CUDA_VISIBLE_DEVICES=1 python ...
```

# 改变文件所有者

```shell
chown
```

# 改变文件访问权

```shell
chmod
```
