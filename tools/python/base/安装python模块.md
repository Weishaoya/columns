使用 pip 安装 python 模块非常方便：

```shell
pip install <模块名>
```

然而有时候老是会遇到一些问题安装失败，下面罗列一些常见问题及其解决方案。

## 问题0：pip版本过低警告

```shell
WARNING: There was an error checking the latest version of pip.
```

虽然只是警告，但是看着总有些不爽，可以通过更新 `pip` 解决：

```shell
python -m pip install --upgrade pip
```

## 问题1：无法连接到代理

```shell
WARNING: Retrying (Retry(total=4, connect=None, read=None, redirect=None, status=None)) after connection broken by 'ProxyError('Cannot connect to proxy.', FileNotFoundError(2, 'No such file or directory'))'
```

这个警告往往会导致无法使用 pip 安装软件包。python 3.8 及一下版本可能存在这个问题，一般通过关闭代理解决。

## 问题2：socket 连接超时

对于频繁出现 `socket.timeout` 的情况，可以考虑下载 wheel 文件之后直接离线安装：

```shell
pip install <wheel文件路径>
```

## 问题3：需要 MSVC 14.0 及以上版本

报错：Microsoft Visual C++ 14.0 or greater is required.

首先尝试更新 `setuptools` 之后重新安装：

```shell
pip install --upgrade setuptools
```

如果依然存在同样的错误，到 https://visualstudio.microsoft.com/visual-cpp-build-tools/ 下载 "Microsoft C++ Build Tools" ，下载并打开后会直接展示 “正在安装 - Visual Studio 生成工具” 页面。选择必要组件并安装（在单个组件中选择最新的 msvc 生成工具）即可。

> vs 生成工具默认安装在 `C:\Program Files (x86)\Microsoft Visual Studio` 目录下。
