
```cpp
/**
 * Segment Tree
 */
class SegTree
{
    vector<LL> tree, lazy;
    void pushUp(int rt) {
        tree[rt] = tree[rt<<1] + tree[rt<<1|1];
    }
    void pushDown(int L, int R, int rt) {
        if (L == R || !lazy[rt]) return;
        LL &v = lazy[rt];
        int m = L+R >> 1;
        tree[rt<<1] += v*(m-L+1);
        tree[rt<<1|1] += v*(R-m);
        lazy[rt<<1] += v;
        lazy[rt<<1|1] += v;
        v = 0;
    }
public:
    SegTree(int n) {
        tree.resize(n<<2);
        lazy.resize(n<<2);
    }
    void build(int L, int R, int rt) {
        if (L == R) {
            scanf("%lld", &tree[rt]);
            return;
        }
        int m = L+R >> 1;
        build(L, m, rt<<1);
        build(m+1, R, rt<<1|1);
        pushUp(rt);
    }
    void add(int x, int y, LL val, int L, int R, int rt){
        if (x <= L && R <= y) {
            tree[rt] += val*(R-L+1);
            lazy[rt] += val;
            return;
        }
        pushDown(L, R, rt);
        int m = L+R >> 1;
        if (x <= m) add(x, y, val, L, m, rt<<1);
        if (y > m) add(x, y, val, m+1, R, rt<<1|1);
        pushUp(rt);
    }
    LL query(int x, int y, int L, int R, int rt) {
        if (x <= L && R <= y) {
            return tree[rt];
        }
        pushDown(L, R, rt);
        int m = L+R >> 1;
        LL ans = 0;
        if (x <= m) ans += query(x, y, L, m, rt<<1);
        if (y > m) ans += query(x, y, m+1, R, rt<<1|1);
        return ans;
    }
};
```
