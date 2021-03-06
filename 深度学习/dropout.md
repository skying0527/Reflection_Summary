# dropout如何作用的？
以p的概率随机的丢掉一些神经元，使得该条链路上的数据不参与loss计算及**反向传播**。**剩余的元素需要除以1-p，保证dropout前后的代价一致**

# L1为什么在深度学习中不常用？
L1和L2正则化，在训练的时候限制权值变大；都是针对模型中参数过大的问题引入惩罚项，依据是奥克姆剃刀原理。
在深度学习中，**L1会趋向于产生少量的特征，而其他的特征都是0增加网络稀疏性**；而L2会选择更多的特征，这些特征都会接近于0，防止过拟合。
**神经网络需要每一层的神经元尽可能的提取出有意义的特征**，而这些特征不能是无源之水，因此L2正则用的多一些。

# 用贝叶斯机率说明Dropout的原理？
通过dropout实现指数级别上的继承父神经网络参数的不同子集模型，使得在有限参数下代表指数数量的子模型成为可能。
单个子模型在面对指定的场景下能有非常好的表现，参数共享又使得剩余的子网络有一个比较好的参数设定。

# 为什么有效？

- dropout使得网络不至于过于复杂，一定避免了减少了单次的参数量降低过拟合的风险，提升了训练速度
- 每次dropout相当于生成了一个参数共享的子网络，子网络的个数是指数级别的相当于训练了无数个子模型
- 每次dropout相当于生成了一个参数共享的子网络，子网络带来的反向传递的结果可以作用在剩余网络上，可被记忆
- dropout之后，可以通过修改input不改网络得到同样的计算结果，换句话说就是增加样本
- 在非线性问题上，**通过学习若干个局部空间的特征会比在全局上寻找学习一个整个空间的特征要好**，而通过dropout构造样本的稀疏性，来增加特征的区分度。

*如果有被问到这个问题，有两种可能第一是你非常优秀，面试官想看你的知识边界；另一种是面试官不想要你，想找个难一点的题目好写面试反馈*

这个地方我只能说自己的理解，这边有几篇论文大家可以去好好看看，有一些自己的体会，因为我自己也不是100%理解，手动狗头。

- A simple way to prevent neural networks from overfitting
- Dropout as data augmentation
- An empirical analysis of dropout in piecewise linear networks
- Improving neural networks by preventing co-adaptation of feature detectors

