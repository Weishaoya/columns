乘法逆元

```cpp
typedef long long LL;
LL qpow(LL a, LL b, LL mod = LLONG_MAX)
{
    a %= mod;
    LL t = 1;
    while (b) {
        if (b&1) t = t*a%mod;
        a = a*a%mod;
        b >>= 1;
    }
    return t%mod;
}

LL inv(LL x, LL p)
{
    return qpow(x, p-2, p);
}
```
