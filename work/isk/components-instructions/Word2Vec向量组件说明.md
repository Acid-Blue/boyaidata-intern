## Word2Vec 向量

### 1. 简介

Word2Vec是一种低维、稠密的词向量方法，包含上下文语境特征。

### 2. 参数面板说明

+ 语言：选择语言类型，支持中文和英文。
+ 词汇限制：由于存储空间有限，对载入的词向量个数进行限制。

### 3. 输入输出桩说明

+ 输入桩：0个。
+ 输出桩：1个，返回数据对象。

### 4. 节点报告

+ 返回已载入词向量的数据对象。

![Word2VecReport](D:\文档\2020-2021-2\文本分析组件\pics\Word2VecReport.png)

### 5. 原理说明

+ Word2Vec向量是通过轻量级的神经网络网络（分为CBOW模型和Skip-gram模型）在大量语料上训练后得到的词嵌入表示。
+ CBOW模型和Skip-gram模型都以经过OneHot编码的语料作为输入。
+ 其中，CBOW模型根据上下文预测当前词语，而Skip-gram根据当前词语预测上下文。
![Word2Vec原理](D:\文档\2020-2021-2\文本分析组件\pics\Word2Vec.png)
+ 经过训练后，从神经网络的权重矩阵 $W$ 可以得到每个词语的低维稠密表示，本组件使用的Word2Vec向量长度均为300。

