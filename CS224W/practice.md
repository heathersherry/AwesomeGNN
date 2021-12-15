## Notes about tools and packages I have used 
1. torch.nn.Embedding
> * 这是一个矩阵类，里面初始化了一个随机矩阵，矩阵的长是字典的大小，宽是用来表示字典中每个元素的属性向量，向量的维度根据你想要表示的元素的复杂度而定。类实例化之后可以根据字典中元素的下标来查找元素对应的向量。
> * https://blog.csdn.net/tommorrow12/article/details/80896331
2. Training Transformer models using Distributed Data Parallel and Pipeline Parallelism [[Link](https://github.com/pytorch/tutorials/blob/master/advanced_source/ddp_pipeline.py)]
> * There is a bug that needs to be addressed: https://github.com/pytorch/pytorch/issues/68407 
3. RNN in PyTorch and torch.nn.utils.rnn.pack_padded_sequence
> * [[Classical tutorial](https://karpathy.github.io/2015/05/21/rnn-effectiveness/)]
> * https://zhuanlan.zhihu.com/p/71732459
4. torch.nn.GRU 
> * https://www.cnblogs.com/duye/p/10590146.html
5. torch.nn.Parameter nn.ParameterList nn.ParameterDict
> * https://blog.csdn.net/Zhaoxi_Li/article/details/105309112
6. torch.randn and torch.rand
> * https://blog.csdn.net/wangwangstone/article/details/89815661
7. torch tensor.view (similar to the reshape function in numpy) 返回和原tensor数据个数相同，但size不同的tensor
> * https://cloud.tencent.com/developer/article/1608350
> * tensor view(-1,xx):如果你不知道你想要多少行，但确定列数，那么你可以将行数设置为-1(你可以将它扩展到具有更多维度的张量。只有一个轴值可以是-1)。这是告诉系统Library：给我一个具有这么多列的张量，并计算实现这一点所需的适当行数
8. torch.sum()
> * [[Good example](https://blog.csdn.net/qq_23262411/article/details/100398449?utm_medium=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase)]
> * what does dim=-1 or -2 mean in torch.sum()? https://stackoverflow.com/questions/59702785/what-does-dim-1-or-2-mean-in-torch-sum
9. torch 矩阵相乘
> * torch.mm(a, b)是矩阵a和b矩阵相乘，比如a的维度是(1, 2)，b的维度是(2, 3)，返回的就是(1, 3)的矩阵
> * torch.mul(a, b)是矩阵a和b对应位相乘，a和b的维度必须相等，比如a的维度是(1, 2)，b的维度是(1, 2)，返回的仍是(1, 2)的矩阵
> * torch.matmul() 永远是最低两维做乘法. https://blog.csdn.net/qsmx666/article/details/105783610
10. torch.ones_like(input, dtype=None, layout=None, device=None, requires_grad=False) → Tensor
> * 返回一个填充了标量值1的张量，其大小与之相同 input。
11. torch.where(condition, x, y)
> * 根据条件，返回从x,y中选择元素所组成的张量。如果满足条件，则返回x中元素。若不满足，返回y中元素。
12. torch.nn.functional.softmax(x,dim)对参数dim的理解
> * https://blog.csdn.net/Will_Ye/article/details/104994504
13. Difference between torch.stack() and torch.cat()  stack: new dimension,cat: given dimension
> * https://stackoverflow.com/questions/54307225/whats-the-difference-between-torch-stack-and-torch-cat-functions
14. torch.norm() 求范数(没有指定p的话就默认求2范数)
> * https://blog.csdn.net/goodxin_ie/article/details/84657975
15. torch.nn.LayerNorm [[Official](https://pytorch.org/docs/stable/generated/torch.nn.LayerNorm.html)]
> * https://stackoverflow.com/questions/59830168/layer-normalization-in-pytorch
16. torch.nn.Linear: Applies a linear transformation to the incoming data [[Official](https://pytorch.org/docs/stable/generated/torch.nn.Linear.html)]
> * 对输入数据做线性变换：y=Ax+b. 注意线性方程中的权重W（形状（out_features，in_features））和偏差b（形状（out_features））是随机初始化的
17. torch.nn.functional.embedding [[Official](https://pytorch.org/docs/stable/generated/torch.nn.functional.embedding.html)]
> * A simple lookup table that looks up embeddings in a fixed dictionary and size.
