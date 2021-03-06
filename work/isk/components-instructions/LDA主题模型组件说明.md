## LDA主题模型

### 1. 简介

潜在狄利克雷分配 （Latent Dirichlet Allocation）是基于贝叶斯理论的经典主题模型。该组件以词袋矩阵或TF-IDF矩阵作为输入。

### 2. 参数面板说明

+ 特征列：输入词袋矩阵或者TF-IDF矩阵（可以通过“所有token”一键勾选）。
+ 主题数：模型主题的个数，为正整数，默认为10。
+ 文档-主题先验：文档-主题分布的超参数 $ \alpha $，默认为 $ \frac {1}{主题数}$。
+ 主题-词语先验：主题-词语分布的超参数 $ \eta $，默认为 $ \frac {1}{主题数}$。
+ 最大迭代次数：训练参数过程中，最大迭代次数，默认为10。
+ 训练方式：分为batch和online两种方式。在batch方式下，
+ Batch大小：
+ 随机种子：为了使得每次运行得到相同结果，应设置随机种子，为正整数，默认为42。

### 3. 输入输出桩说明：

+ 输入桩：1个，连接数据对象。
+ 输出桩：3个。左侧输出桩返回已训练的LSI模型，中间输出桩返回包含各样本主题标签的数据对象，右侧输出桩返回原数据对象。

### 4. 节点报告

+ 返回主题成分矩阵（主题在各个token上的载荷）、主题关键词（每个主题选取最有代表性的5个关键词）、困惑度（perplexity）、实际迭代次数。

+ 困惑度（perplexity）越小，说明各主题重合度越低，建模效果越好。

![](D:\文档\2020-2021-2\文本分析组件\pics\LatentDirichletReport.png)

### 5. 原理说明

+ LDA模型从文本生成的角度，将文本视为从概率空间中重复采样的结果。
+ 该模型假设每一个文档有主题分布，每个主题有词语分布，模型从语料中学习这两种概率分布，以使后验概率最大。
+ LDA模型的数学描述如下：
  + 对于每个主题 $ k ∈ K$ ， $ Dirichlet (\eta)$ 中采样 $ \beta_k$
  + 对于每个文档 $ d ∈ D$，从$ Dirichlet (\alpha)$ 中采样 $ \theta_d $
  + 对于文档 $ d$ 中的每个词语 $ i $，有
    +  $ z_{di} \sim Multinomial( \theta_d)$ 
    + $ w_{ij} \sim Multinomial ( \beta_{z_{di}})$ 

  + 注：$Dirichlet$ 表示狄利克雷分布，$ Multinomial $ 表示多项式分布，这两种概率分布为共轭分布。

+ LDA用图模型表示如下：

![LDA模型原理](D:\文档\2020-2021-2\文本分析组件\pics\lda_model_graph.png)