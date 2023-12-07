# 字典树的结构

想象一颗深度无限的 26 叉树，树上的每个结点都有 26 条出边，将这 26 条出边依次编号为 $a,b,\cdots,z$ 。

任意给定一个仅由小写英文字母构成的字符串，我们都可以将其视为从根节点到某个结点的路径。于是一个字符串与从根结点到任意节点的路径一一对应。

我们可以在结点中存储与字符串前缀相关的信息，如：
- 以某串为前缀的字符串个数

链表版字典树

```cpp
class Trie
{
    Trie* next[26];
    int num;
public:
    Trie() {
        for (int i = 0; i < 26; ++i) next[i] = NULL;
        num = 0;
    }
    void insert(char *s) {
        Trie *p = this;
        ++ p->num;
        for (int i = 0; s[i]; ++i) {
            int t = s[i]-'a';
            if (p->next[t] == NULL) p->next[t] = new Trie;
            p = p->next[t];
            ++ p->num;
        }
    }
    int find(char *s) {
        Trie *p = this;
        for (int i = 0; s[i]; ++i) {
            int t = s[i]-'a';
            if (p->next[t] == NULL) return 0;
            p = p->next[t];
        }
        return p->num;
    }
};
```

数组版字典树

```cpp
#include <vector>
using namespace std;
class Trie
{
    int cnt;
    vector<vector<int> > tree;
    vector<int> num;
public:
    Trie(int n) {
        cnt = 0;
        tree.resize(n, vector<int>(26));
        num.resize(n);
    }
    void insert(char *s) {
        int p = 0;
        ++num[p];
        for (int i = 0; s[i]; ++i) {
            int t = s[i]-'a';
            if (!tree[p][t]) tree[p][t] = ++cnt;
            p = tree[p][t];
            ++num[p];
        }
    }
    int find(char *s) {
        int p = 0;
        for (int i = 0; s[i]; ++i) {
            int t = s[i]-'a';
            if (!tree[p][t]) return 0;
            p = tree[p][t];
        }
        return num[p];
    }
};
```
