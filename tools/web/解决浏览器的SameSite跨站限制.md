当代浏览器在请求跨域资源时会限制 set-cookie 字段。为了解决这一问题，应将资源链接设为 https 协议，并在 cookie 中携带 

```
SameSite=None; Secure
```

# 参考

[^1]: 完美解决Chrome Cookie SameSite跨站限制. https://www.mostintelligentape.com/2022/03/07/%E6%8A%80%E6%9C%AF%E6%89%8B%E5%86%8C/2022-03-08-chrome-cookie-%E8%B7%A8%E7%AB%99/.