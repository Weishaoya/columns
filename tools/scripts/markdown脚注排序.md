有时候希望脚注按照在文章中的引用顺序排序，写文章的过程中手动维护有点繁琐，于是考虑“写文章时放飞自我，写完之后脚本排序”。

需求：

- 对 `[^n]` 和 `[^n]:` 形式的脚注按在文中的引用顺序进行排序。
- 对尚未引用的脚注保持相对位置不变，并放在已经引用的脚注之后。
- 对尚未定义的引用保持label不变，如果编号重排时与label冲突则将编号顺延。

假设

- 正则表达式 `\[\^\d+\]` 可以且仅可以匹配到所有脚注及其引用。
- 第一行没有脚注，每个脚注独占一行且顶格写。具体来说，正则表达式 `\n\[\^\d+\]:.*` 可以且仅可以匹配到所有脚注。



```python
import os
import shutil
import re


def recover(filename):
    backup_filename = filename + '.backup'

    if os.path.exists(backup_filename):
        print('Recovering.....')
        shutil.copy(backup_filename, filename)
        os.remove(backup_filename)
        print('Done.')
    else:
        print('No backup file for recovery.')


def footnote_sorting(filename):
    backup_filename = filename + '.backup'

    # 防呆处理
    if os.path.exists(backup_filename):
        file_mtime = os.path.getmtime(filename)
        backup_file_mtime = os.path.getmtime(backup_filename)
        if abs(file_mtime - backup_file_mtime) < 1:
            """备份文件与源文件修改时间差不超过1s，认为源文件没有修改，为避免覆盖备份文件，直接返回"""
            print('Already sorted.')
            return
        
    print('Sorting.....')
        
    # 备份文件
    shutil.copy(filename, backup_filename)

    # 读取内容
    with open(filename, 'r', encoding='utf-8') as f:
        content = f.read()
    
    # 重新编号
    citation_regex  =   '\[\^(\d+)\]'
    order = dict()
    order_id = 0
    def get_order(matched):
        nonlocal order, order_id
        label = matched.group(1)
        if label not in order:
            order_id += 1
            order[label] = str(order_id)
        return f'[^{order[label]}]'
    content = re.sub(citation_regex, get_order, content)

    # 交换脚注次序
    footnotes_regex = '\n\[\^(\d+)\]:(.*)'

    order_id = -1
    footnotes = re.findall(footnotes_regex, content)
    footnotes = sorted(footnotes, key=lambda x: int(x[0]))
        
    def get_footnote(matched):
        nonlocal footnotes, order_id
        order_id += 1
        return f'\n[^{footnotes[order_id][0]}]:{footnotes[order_id][1]}'
    content = re.sub(footnotes_regex, get_footnote, content)

    # 保存内容
    with open(filename, 'w', encoding='utf-8') as f:
        f.write(content)

    print('Done.')
    

if __name__ == '__main__':
    import sys
    sys.argv.append('data/test.md')
    filename = sys.argv[1]
    recover(filename)
    footnote_sorting(filename)
```

