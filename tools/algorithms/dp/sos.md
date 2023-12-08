# 引入

给定整数数组 $a_0,a_1,\cdots,a_{2^n-1}$ ，需要进行 $q$ 次查询。

每次查询给定整数 $x(0\le x \le 2^n-1)$ ，查询数组 $a$ 中所有下表是 $x$ 的子集的位置的数值之和。即求 $\sum_j [x | j=x]a_j$ ，其中 $|$ 是按位或操作。

朴素的算法可以对每次查询遍历依次数组 $a$ ，时间复杂度为 $O(q\cdot |a|)=O(q\cdot 2^n)$ .

对每次查询仅遍历 $j$ 的子集可将时间复杂度将为 $O(q\cdot 2^{|j|})$ 其中 $|j|$ 代表整数 $j$ 中 $1$ 的个数。

# Sum Over Subsets

Sum Over Subsets dp 算法首先以 $O(n\cdot 2^n)$ 的复杂度求出所有集合对应的子集和然后以 $O(1)$ 的复杂度进行每次查询，总的时间复杂度为 $O(n\cdot 2^n + q)$。Sum Over Subsets dp 算法描述如下：

定义 $f(x, b)$ 为 $x$ 的子集中低 $b$ 位与 $x$ 相同的集合所对应的 $a$ 值之和。

由定义知

$$
f(x,b)=\begin{cases}
a_x, & b = n, \\
f(x,b+1), & 0\le b \le n-1\land x\&2^b =0, \\
f(x,b+1)+f(x-2^b,b+1) & 0\le b \le n-1\land x\&2^b \ne 0
\end{cases}
$$

其中 $\&$ 是按位与操作。

```cpp
// 数组a
vector<int> a(1 << n);

// sos dp
for (int i = 0; i < (1 << n); ++i) {
    f[i][n] = a[i];
}
for (int b = n - 1; b >= 0; --b) {
    f[i][b] = f[i][b + 1];
    if (i & (1 << b)) f[i][b] += f[i - (1 << b)][b + 1];
}
```

由于 $f(\cdot, b)$ 的状态仅与 $f(\cdot, b + 1)$ 有关，且查询仅需用到 $f(\cdot, 0)$，因此可以采用滚动数组优化 sos dp 的空间。

```cpp
// sos dp
for (int i = 0; i < (1 << n); ++i) {
    f[i] = a[i];
}
for (int b = n - 1; b >= 0; --b) {
    if (i & (1 << b)) f[i] += f[i - (1 << b)];
}
```

# Sum Over Supersets

将前述“子集”换成成“超集”，情况类似

```cpp
// sos dp
for (int i = 0; i < (1 << n); ++i) {
    f[i] = a[i];
}
for (int b = n - 1; b >= 0; --b) {
    if (!(i & (1 << b))) f[i] += f[i - (1 << b)];
}
```

# 参考

[^1]: SOS Dynamic Programming [Tutorial]. https://codeforces.com/blog/entry/45223.