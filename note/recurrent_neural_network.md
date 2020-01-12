# recurrent neural network

**循环网络(Recurrent Neural Network)** RNN 用于处理数列数据神经网络。

模型内共享参数容易泛化

RNN的基本
$$
a^{(t)} = b + Wh^{(t-1)} + Ux^{(t)}
$$

$$
h^{(t)} = tanh(a^{(t)})
$$

$$
o^{(t)} = c + Vh^{(t)}
$$

$$
\hat{y}^{(t)} = softmax(o^{(t)})
$$

$a$与$h$有循环

$b$和$c$、$U$、$V$、$W$分别对应输入到隐藏，隐藏到输出和隐藏到隐藏的连接。与$x$序列配对的$y$的总损失就是所有时间步的损失之和。例如$L^{(i)}$为给定$x^{(1)},x^{(2)},\cdots,x^{(\tau)}$后$y^{(t)}$的负对数似然
$$
L(\{x^{(1)},\cdots,x^{(\tau)}\},\{y^{(1),\cdots,y^{(\tau)}}\})
$$

$$
=\sum_{t}L^{(t)}
$$

$$
=-\sum_{t}\log{p_{model(y^{(t)} | \{x^{(1)},\cdots,x^{(t)}\})}}
$$

隐藏单元之间存在循环的网络非常强大，但训练代价也很在。

通常，将RNN的输出解释为一个概率分布，通常使用与分布相关联的交叉熵定义损失。均方误差是与单位高斯分布的输出相关联的交叉熵损失。

无输入的RNN

基于上下文的RNN序列建模

**双向循环网络：**场景，输出$y^{(t)}$预测依赖整个输入序列。例如手写识别，语音识别，生物信息学

大多数RNN：

1. 从输入到隐藏状态
2. 从前一状态到下一状态
3. 从隐藏状态到输出

**深度循环网络：**RNN状态分为多层可能有显著好处

**递归神经网络：**构造为深的树状结构而不是RNN的链状结构。成功应用：自然语言处理，计算机视觉；

递归神经网络明显优势：对于具有相同长度$\tau$的序列，深度（通过非线性操作的组合数量来衡量）可急剧地从$\tau$减小为$O(\log(\tau))$，有助于解决长期依赖。

递归神经网络未解决的问题：如何以最佳的方式构造树
