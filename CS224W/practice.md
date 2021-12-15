## Notes about tools and packages I have used 
1. Torch.nn.Embedding
> * 这是一个矩阵类，里面初始化了一个随机矩阵，矩阵的长是字典的大小，宽是用来表示字典中每个元素的属性向量，向量的维度根据你想要表示的元素的复杂度而定。类实例化之后可以根据字典中元素的下标来查找元素对应的向量。
> * https://blog.csdn.net/tommorrow12/article/details/80896331
2. Training Transformer models using Distributed Data Parallel and Pipeline Parallelism [[Link](https://github.com/pytorch/tutorials/blob/master/advanced_source/ddp_pipeline.py)]
> * There is a bug that needs to be addressed: https://github.com/pytorch/pytorch/issues/68407 
