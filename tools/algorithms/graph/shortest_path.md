# dijkstra 单源最短路算法

## 堆优化的 dijkstra

```cpp
/**
 * Dijkstra 算法计算从 s 出发的单源最短路，堆优化
 * @param g 原图的邻接表
 * @param s 源点
 * @param inf 认定是无穷大的数值，默认 INT_MAX
 * @return 从源点 s 到顶点 0, 1, 2, ..., n - 1 的单源最短路
 */
vector<int> heap_dijkstra(const vector<vector<Edge>> &g, const int s, const int inf = INT_MAX) {
    int n = g.size();
    vector<int> d(n, inf);
    priority_queue<node> heap;
    d[s] = 0;
    heap.push({s, d[s]});
    while (!heap.empty()) {
        auto t = heap.top();
        heap.pop();
        if (d[t.v] !=  t.w) continue;
        for (auto &e : g[t.v]) {
            assert(e.w >= 0);  // 不应出现负权
            if (d[e.to] > t.w + e.w) {
                d[e.to] = t.w + e.w;
                heap.push({e.to, d[e.to]});
            }
        }
    }
    return d;
}
```

# Bellman-Ford 算法

## 堆优化的 Bellman-Ford 算法 —— SPFA

```cpp
/**
 * SPFA 算法计算从 s 出发的单源最短路，Bellman-Ford 算法的队列优化
 * @param g 原图的邻接表
 * @param s 源点
 * @param inf 认定是无穷大的数值，默认 INT_MAX
 * @return 从源点 s 到顶点 0, 1, 2, ..., n - 1 的单源最短路
 */
vector<int> spfa(vector<vector<Edge>> &g, const int s, const int inf = INT_MAX) {
    int n = g.size();
    vector<bool> vis(n);  // 避免重复入队
    vector<int> cnt(n);  // 检测负环
    vector<int> d(n, inf);
    d[s] = 0;
    queue<int> q;
    q.push(s);
    vis[s] = true;
    while (!q.empty()) {
        int u = q.front();
        q.pop();
        vis[u] = false;
        for (auto &e : g[u]) {
            if (d[e.to] > d[u] + e.w) {
                d[e.to] = d[u] + e.w;
                cnt[e.to] = cnt[u] + 1;
                if (cnt[e.to] == n) return {};
                if (!vis[e.to]) {
                    q.push(e.to);
                    vis[e.to] = true;
                }
            }
        }
    }
    return d;
}
```

# Floyd 全源最短路。

> 依次通过顶点 $1,2,\cdots,n$ 中转更新 $i$ 到 $j$ 的最短路。

```cpp
/**
 * Floyd 算法计算原图的全源最短路
 * @param d 原图的邻接矩阵
 * @param inf 认定是无穷大的数值，默认 INT_MAX
 * @return 全源最短路
 */
vector<vector<int>> floyd(vector<vector<int>> d, const int inf = INT_MAX) {
    int n = d.size();
    for (int k = 0; k < n; ++k)
        for (int i = 0; i < n; ++i)
            for (int j = 0; j < n; ++j)
                if (d[i][k] != inf && d[k][j] != inf)
                    d[i][j] = min(d[i][j], d[i][k] + d[k][j]);
    return d;
}
```
