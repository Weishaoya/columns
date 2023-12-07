> 当前版本：4.1.2

用 `gradio` 命令运行时出错

```text
UnicodeDecodeError: 'gbk' codec can't decode byte 0xb0 in position 597: illegal multibyte sequence
```

在当前python环境的 site-packages\gradio\cli\commands\reload.py 下找到 `_setup_config` ，将

```python
app_text = Path(original_path).read_text()
```

改为

```python
app_text = Path(original_path).read_text(encoding='utf-8')
```
