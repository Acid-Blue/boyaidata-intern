## GloVe 向量

### 1. 简介

GloVe(全局向量)是一种低维、稠密的词向量方法，包含上下文语境特征。

### 2. 参数面板说明

+ 语言：选择语言类型，支持中文和英文。
+ 词汇限制：由于存储空间有限，对载入的词向量个数进行限制。

### 3. 输入输出桩说明

+ 输入桩：0个。
+ 输出桩：1个，返回数据对象。

### 4. 节点报告

+ 返回已载入词向量的数据对象。

![Glove报告](D:\文档\2020-2021-2\文本分析组件\pics\GloveReport.png)

### 5.原理说明

+ GloVe向量是基于词共现矩阵训练得到的低维、稠密的词向量。
+ Glove模型定义为

$$
J= \sum \limits_{i,j = 1}^V f(X_{ij})({w_i}^T \widetilde{w_j}+b_i-b_j-logX_{ij})^2
$$

​       其中 $X$ 为词共现矩阵， $w_i$ 为词向量，$\widetilde w_i$ 为上下文向量，$f(·)$ 为加权函数，$b$ 为偏差项(bias)。

+ 该模型可以通过最小二乘法求得参数，被认为结合了全局矩阵分解方法（如LSI）和局部上下文窗口方法（如CBOW）两类方法的优点。
+ 算法细节请参考：[Global Vectors for word representation](https://nlp.stanford.edu/pubs/glove.pdf)

