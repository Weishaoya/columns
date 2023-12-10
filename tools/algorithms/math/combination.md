$$
\begin{aligned}
C_n^m&=\frac{n!}{m!(n-m)!}\\
&=\frac{n-m+1}{m}\cdot C_n^{m-1}\\
&=\cdots \\
&=\frac{n-m+1}{m}\cdots \frac{n - i + 1}{i} \cdot C_n^{i-1}\\
&=\cdots \\
&=\frac{n-m+1}{m}\cdots \frac{n - i + 1}{i}\cdots \frac{n - 1 + 1}{1} \cdot C_n^{0}\\
\end{aligned}
$$

```cpp
long long C(int n, int m) {
    if (m > n - m) m = n - m;
    long long ans = 1;
    for (int i = 1; i <= m; ++i) {
        ans = ans * (n - i + 1) / i;
    }
    return ans;
}

int C(int n, int m, int mod) {
    if (m > n - m) m = n - m;
    int ans = 1;
    for (int i = 1; i <= m; ++i) {
        ans = 1LL * ans * (n - i + 1) % mod * qpow(i, mod - 2, mod) % mod;
    }
    return ans;
}
```

- 对 $n$ 个苹果进行划分，有 $2^{n-1}$ 种分法。因为 $n$ 个苹果有 $n-1$ 个间隔，每个间隔有取或不取两种状态。
