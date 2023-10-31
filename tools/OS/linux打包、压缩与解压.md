# .gz 文件

`gzip` 命令通常用于压缩单个文件。每次运行 `gzip` 命令，它将压缩一个文件，并且通常会替换原始文件，留下一个扩展名为 `.gz` 的压缩文件。

压缩单个文件

```shell
gzip <filename>
```

解压缩 `<filename>.gz`

```shell
gunzip <filename>.gz
```



# .tar 文件

归档多个文件或文件夹

```shell
tar -cvf <folder>.tar <folder>
```

查看 `<folder>.tar`

```shell
tar -tf <folder>.tar
```

从 `folder.tar` 中提取文件

```shell
tar -xvf <folder>.tar
```

选项说明：

- `-c` create a new archive
- `-t` list the contents of an archive
- `-x` extract files from an archive
- `-v` verbosely list files processed
- `-f ARCHIVE` use archive file or device ARCHIVE



# .tar.gz 文件

压缩多个文件或文件夹

```shell
tar -zcvf <folder>.tar.gz <folder>
```

查看 `<folder>.tar.gz`

```shell
tar -tf <folder>.tar.gz
```

从 `folder.tar.gz` 中提取文件

```shell
tar -zxvf <folder>.tar.gz
```

选项说明：

`-z` use gzip to compress or uncompress.



# .zip 文件

压缩

```shell
zip -r <folder>.zip folder
```

解压缩 `<folder>.zip` 

```shell
unzip <folder>.zip
```

选项说明：

- `-r` recurse into directories
