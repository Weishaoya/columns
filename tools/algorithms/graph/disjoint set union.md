
```cpp
#include <vector>
using namespace std;
/**
 * Disjoint Set Union
 */
class DSU
{
    vector<int> s;
    int cnt;  // 记录集合个数
 public:
    DSU(int n) {
        cnt = n;
        s.resize(n+1);
        for (int i = 1; i <= n; ++i) s[i] = i;  // 初始化
    }
    int find(int x) {
        if (x != s[x]) s[x] = find(s[x]);  // 路径压缩
        return s[x];
    }
    bool unite(int u, int v) {
        int x = find(u);
        int y = find(v);
        if (x != y) {
            s[y] = x;
            --cnt;
            return true;
        }
        return false;
    }
    int getCnt() {
        return cnt;
    }
};
```
