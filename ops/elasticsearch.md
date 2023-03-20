# <!-- -->

# 索引变成了只读怎么办？
kibana查询时，报错如下：
<img src="https://user-images.githubusercontent.com/1846319/226222286-794fc4a8-0a46-4a5d-b5b6-6151998431eb.png" width="400px">

```
index [.async-search] blocked by: [TOO_MANY_REQUESTS/12/disk usage exceeded flood-stage watermark, index has read-only-allow-delete block];
```

原因很明显，磁盘没空间了。这个时候你可以删除不需要的索引数据，或者给elasticsearch 的pvc扩容。下面来说一下怎么给pvc扩容。

### 步骤一：修改pv资源

<img width="600px" src="https://user-images.githubusercontent.com/1846319/226283640-07831de6-bfb5-4124-8df6-2247ad84cd04.png">

一定要记得修改pv回收策略为retain，否则可能删除pvc时导致pv自动删除，引起数据丢失

### 步骤二：删除原来的pvc资源重建

<img width="669" alt="image" src="https://user-images.githubusercontent.com/1846319/226285774-78f08a42-3d1e-42ed-92c4-322a8137bd52.png">
