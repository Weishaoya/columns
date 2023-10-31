查看执行策略：

```shell
Get-ExecutionPolicy
```

更改执行策略：

```shell
Set-ExecutionPolicy <策略名称>
```

<策略名称> 包括：

1. `Restricted`（默认值）：不允许运行脚本。只允许运行命令。
2. `AllSigned`：只允许运行经数字签名的脚本。
3. `RemoteSigned`：允许运行本地创建的脚本，但要求远程下载的脚本必须经过数字签名。
4. `Unrestricted`：允许运行任何脚本，没有数字签名的限制。这是最不安全的选项，应谨慎使用。
5. `Bypass`：忽略执行策略，允许运行任何脚本。



