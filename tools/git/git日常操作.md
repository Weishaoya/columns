# 删除远端分支

```shell
git push -d <origin> <branch>
```

# 分支重命名

```shell
git branch -m <old-branch> <new-branch>
```

如果当前已在 `<old-branch>`，可以省略该项。

# 将本次修改的内容添加到上次提交中

```shell
git commit --amend
```

# 合并分支

将 work 分支合并到 dev 分支

首先在 work 分支 rebase dev 并解决冲突

```shell
git checkout work
git rebase dev
```

然后切换到 dev 分支 merge work

```shell
git checkout dev
git merge work
```
