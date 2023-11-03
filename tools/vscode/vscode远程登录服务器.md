# 安装插件

vscode的插件安装在 `~/.vscode/extensions` 目录下，可以在有网的环境下安装插件后把上述目录中的插件复制到没网机器的相同位置[^1]。

# 连接远程主机

在本地不能访问外网的情况下vscode无法下载 `vscode-server.tar.gz` 从而导致 `XHR failed` 。

可以首先在 `Help>About` 中查看 `Commit` ，然后手动从 `https://update.code.visualstudio.com/commit:${Commit}/server-linux-x64/stable` 中下载 `vscode-server-linux-x64.tar.gz` 并上传到服务器，然后执行

```shell
tar zxvf vscode-server-linux-x64.tar.gz -C ~/.vscode-server/bin/${Commit} --strip 1
```

再次连接即可[^2][^3]。



# 参考

[^1]: Vscode离线安装插件的方法. https://www.cnblogs.com/hwy6/p/15930217.html. 
[^2]: VS Code Server的离线安装过程. https://zhuanlan.zhihu.com/p/294933020.
[^3]: How can I install vscode-server in linux offline. https://stackoverflow.com/questions/56671520/how-can-i-install-vscode-server-in-linux-offline.

