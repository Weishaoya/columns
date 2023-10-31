# 安装

> miniconda 与 anaconda 安装其一即可。

## 安装 miniconda 并激活

```shell
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
# ~/miniconda3/bin/conda init  # 激活，可选
```

## 安装 anaconda 并激活

> 在不能访问外网得情况下可以考虑安装 anaconda ，curl 可以通过代理下载。下面以 Anaconda3-2023.09-0-Linux-x86_64.sh 为例。最新版可在 https://www.anaconda.com/download#downloads 下载

``` shell
curl -O https://repo.anaconda.com/archive/Anaconda3-2023.09-0-Linux-x86_64.sh
bash Anaconda3-2023.09-0-Linux-x86_64.sh
# ~/anaconda3/bin/conda init  # 激活，可选
```

# 换源

```shell
vim ~/.condarc
```

```plain text
channels:
  - defaults
show_channel_urls: true
default_channels:
  - http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
  - http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
  - http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
custom_channels:
  conda-forge: http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  msys2: http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  bioconda: http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  menpo: http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  pytorch: http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  simpleitk: http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
```

# conda 命令

## 查看帮助

```shell
conda -h
```

## 创建名为 `ENV_NAME` 的环境

```shell
conda create -n ENV_NAME
```

## 激活名为 `ENV_NAME` 的环境

```shell
conda activate ENV_NAME
```

## 退出当前环境

```shell
conda deactivate
```

# conda env 命令

## 查看帮助

```shell
conda env -h
```

## 环境列表

```shell
conda env list
```

## 删除名为 `ENV_NAME` 的环境

```shell
conda env remove -n ENV_NAME
```

