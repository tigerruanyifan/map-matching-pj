# map-matching-pj

### 怎么做的
- 网格索引
- 最短路确定转移概率
- 维特比算法寻找最优解


### 自己认为做得比较好的地方
- 代码写得比较规范，基本上是按照 Google 的文档标准写的，也不会有 warning，命名什么的都还可以。

- 分区比较明显，结构较为清晰。首先是常量和全局变量，然后是工具函数，再然后是数据结构，最后是主函数。其中由于是单文件，为了节省代码长度与修改的成本，都用 struct，同时不作前置声明，然后函数尽量拿出来单独写，这样就不会遇到交叉引用的问题。

- 充分利用了道路信息。道路中难以利用的信息主要是道路的等级，我根据 openstreetmap 的数据和中国官方的数据，大致确定了不同等级的道路的限速比例，这样可以用车速与限速的关系进行剪枝。同时，我们也可以倾向于认为，在干道上的概率会比较大，我们就可以根据道路等级给概率计算增加权重，这在处理低频数据时很有用。

- 考虑到了一些边界情况。

### 一些代码的细节

```cpp
#define pb push_back
```
这里本来想用个 ```emplace_back```，据说比较快，但是不知道为啥有的对象没法用。

```cpp
using ld = double;
```

本来 ```ld``` 是 ```long double``` 的缩写，但是会在一些点处超时，就都用 ```double```。

### Differences in two source files
- Different Distance functions
- Hyperparameters
- Some detailed comments in Chinese
- Minor changes
