# ssh 免密登录

1. 确认可以正常登录服务器

   ```shell
   ssh <username>@<server_ip>
   ```

2. 生成 ssh 密钥对

   ```shell
   ssh-keygen -t rsa
   ```

    `~/.ssh` 目录中会出现公钥（`id_rsa.pub`）和私钥（`id_rsa`）文件。

3. 将公钥复制到远程服务器。对于 Linux 用户，可以直接执行命令行

    ```shell
    ssh-copy-id <username>@<server_ip>
    ```

    对于 Windows 用户，需要手动复制公钥并添加到远程服务器的`~/.ssh/authorized_keys`文件中。

4. 免密登录

    ```shell
    ssh <username>@<server_ip>
    ```



# ssh 别名登录

在配置文件 `~/.ssh/config` 中添加

```
Host <别名>
    HostName <远程服务器的主机名或IP地址>
    User <用户名>
    IdentityFile ~/.ssh/id_rsa  # SSH私钥文件的路径
```

> - 如果不明确指定 IdentityFile 字段， SSH 客户端会按照一定的规则查找默认的私钥文件
>
> - 如果先设置别名登录，再设置免密登录，可以将命令中的 `<username>@<server_ip>` 全部替换为 `<别名>`。

