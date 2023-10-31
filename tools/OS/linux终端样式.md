查看环境变量 `PS1` .

```shell
vim ~/.bashrc
```

找到 `force_color_prompt=yes` 并取消注释

将提示符终端的主机名替换为其它内容

```
PS1=$(echo "$PS1" | sed 's/\\h/A40/g')
```

