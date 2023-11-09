git 一般依次从3个位置加载配置文件

- `/etc/gitconfig` 文件。Windows上一般是 `D:/programs/Git/etc/gitconfig`
- `~/.gitconfig` 或 `~/.config/git/config` 文件
- `.git/config` 文件

可通过命令查看所有配置项及配置项所在文件：

```shell
git config --list --show-origin
```

当篇多处配置冲突时，靠后的配置生效。



# 常用配置

## 配置用户名和邮箱

安装git后需要通过

```shell
git config --global user.name 用户名
git config --global user.email 用户邮箱
```

在 `~/.gitconfig` 中设置用户名和邮箱。

## 中文显示异常配置

默认情况下包含中文的文件名会用双引号包裹，并且其中的中文字符会以转义字符的形式展示。可通过配置

```shell
git config --global core.quotePath false
```

解决。如果配置后出现中文乱码，那可能是控制台的问题，需要寻求控制台中文乱码的解决方案。



# 参考

[^1]: 起步 - 初次运行 Git 前的配置. https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%88%9D%E6%AC%A1%E8%BF%90%E8%A1%8C-Git-%E5%89%8D%E7%9A%84%E9%85%8D%E7%BD%AE.
[^2]: git 显示中文和解决中文乱码. https://zhuanlan.zhihu.com/p/133706032.

