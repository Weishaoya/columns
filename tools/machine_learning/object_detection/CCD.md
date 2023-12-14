
# 自监督的文本分割任务

获取文本掩码伪分割图 $M_{gt}$ ：通过 $k-means$ 算法将黑白图像中的像素点分成两类。分类之后根据图像边缘像素点的类别判断前景和背景。

自监督的文本分割任务：使用深度学习模型对图像进行文本分割，得到文本分割图 $M_{seg}$ 。使用文本掩码伪分割图 $M_{gt}$ 对文本分割器进行监督。

# 基于连通性的字符分割任务

基于连通性聚类的字符分割任务：获取文本分割图 $M_{seg}$ 之后，注意到单个字符的像素点几乎是连通的，于是采用一种基于连通性的空间聚类算法进行字符分割，分割出的字符数最多为 $26$ ，具体做法如下：

```python
def label(mask):
    zero_ = np.zeros((26, mask.shape[0], mask.shape[1])).astype(np.uint8)
    zero = np.zeros((26, mask.shape[0], mask.shape[1])).astype(np.uint8)
    cluster = measure.label(mask)
    categorys = np.unique(cluster)
    loc = []
    i = 0
    for cate in categorys:
        if cate == 0:
            continue
        sub_cluster = cluster == cate
        if sub_cluster.sum() >= 30:
            loc.append(np.where(sub_cluster)[1].mean())
            zero_[i, sub_cluster] = 1
            i += 1
            if i >= 26:
                break
    index = np.argsort(loc)
    for i, new_index in enumerate(index):
        zero[i] = zero_[new_index]
    return zero
```

# 损失：
- 自监督的文本分割任务 loss
- 字符级对齐 loss：根据上述字符分割任务的结果，可以得出每张图片的字符个数信息，根据字符个数信息计算损失。
