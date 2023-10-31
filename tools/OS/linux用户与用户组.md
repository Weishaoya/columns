# 用户相关操作

用户的创建、修改与删除：`useradd`, `usermod`, `userdel`

用户组的创建、修改与删除： `groupadd`, `groupmod`, `groupdel`

创建用户并将其添加到 sudo 组：

```
sudo adduser <username>
sudo usermod -aG sudo <username>
```

修改密码：

```
passwd
```

切换用户：

```
su <username>
```



# 用户相关文件

`/etc/passwd` 文件是一个包含有关系统用户的基本信息的文本文件。每个用户都在这个文件中占据一行。字段名有用户名、密码、UID、GID、用户说明、主目录、登录 Shell 。

`/etc/group` 文件是用于存储系统用户组信息的文本文件。这个文件包含了有关用户组的信息，每个用户组占据一行。字段名有 组名、密码、GID、组成员。

