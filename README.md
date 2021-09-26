
## Tutorials, Lectures, Surveys, and Notes
1. Stanford CS224W: Machine Learning with Graphs [[Course Website](http://web.stanford.edu/class/cs224w/)] [[Youtube](https://www.youtube.com/playlist?list=PLoROMvodv4rPLKxIpqhjhPgdQy7imNkDn)]
> * My Notes: [[1-5](https://github.com/heathersherry/GNN/blob/main/CS224W/Stanford_CS224W_1-5.md)] [[6-8](https://github.com/heathersherry/GNN/blob/main/CS224W/Stanford_CS224W_6-8.md)] [[9-11](https://github.com/heathersherry/GNN/blob/main/CS224W/Stanford_CS224W_9-11.md)] [[12-17](https://github.com/heathersherry/GNN/blob/main/CS224W/Stanford_CS224W_12-17.md)]
2. Graph neural networks: A review of methods and applications (AI Open 2020) [[Paper](https://www.sciencedirect.com/science/article/pii/S2666651021000012)]

## Papers (Outline)
* __Classical Models__ [[Link](https://github.com/heathersherry/GNN/blob/main/README.md#classical-models)]
* __GNN Efficiency and Scalability__ [[Link](https://github.com/heathersherry/GNN#gnn-efficiency-and-scalability)]
* __HGNN__ [[Link](https://github.com/heathersherry/GNN#hgnn)]
* __GNN Explanability__ [[Link](https://github.com/heathersherry/GNN#gnn-explanability)]
* __Spatial Temporal GNN__ [[Link](https://github.com/heathersherry/GNN#spatial-temporal-gnn)]
* __GNN Applications__ [[Link](https://github.com/heathersherry/GNN#gnn-applications)]
* __GNN in Database Community__ [[Link](https://github.com/heathersherry/GNN#gnn-in-database-community)]


## Classical Models
1. `GCN` [[Notes from the Author](http://tkipf.github.io/graph-convolutional-networks/)]
2. `GraghSAGE`
3. `GAT`
4. `GIN`
5. `RGCN`

## GNN Efficiency and Scalability
1. Adaptive Sampling Towards Fast Graph Representation Learning (NeurIPS 2018) [[Paper](https://papers.nips.cc/paper/2018/file/01eee509ee2f68dc6014898c309e86bf-Paper.pdf)]
2. `GraphSAINT` GraphSAINT: Graph Sampling Based Inductive Learning Method (ICLR 2020) [[Paper](https://arxiv.org/pdf/1907.04931.pdf)] [[Code](https://github.com/GraphSAINT/GraphSAINT)]
3. Performance Adaptive Sampling Strategy Towards Fast and Accurate Graph Neural Networks (KDD 2021) [[Video](https://www.youtube.com/watch?v=uRxF-xLo60o)]
4. Scaling Up Graph Neural Networks Via Graph Coarsening (KDD 2021)
5. `SimplifiedGCN`
6. `ClusterGCN`
7. `GAMLP` Graph Attention Multi-Layer Perceptron [[Code](https://github.com/PKU-DAIR/GAMLP)] [[Notes](https://mp.weixin.qq.com/s/tGss6m22xABWqhJPl4P9aw)]

### Sampling Methods
Random Sampling
1. `GraphSAGE` GraphSage: Inductive Representation Learning on Large Graphs (NeurIPS 2017) [[Paper](https://arxiv.org/pdf/1706.02216.pdf)]

Importance Sampling
1. `Fast-GCN` FastGCN: Fast Learning with Graph Convolutional Networks via Importance Sampling (ICLR 2018) [[Paper](https://arxiv.org/pdf/1801.10247.pdf)]
2. `LADIES`
3. `AS-GCN`
4. `GCN-BS`


## HGNN
1. `simpleHGN` Are we really making much progress? Revisiting, benchmarking, and refining heterogeneous graph neural networks (KDD 2021) [[Paper](https://keg.cs.tsinghua.edu.cn/jietang/publications/KDD21-Lv-et-al-HeterGNN.pdf)] [[Code and data](https://github.com/THUDM/HGB)]
2. `OpenHGNN` An open-source toolkit for Heterogeneous Graph Neural Network(OpenHGNN) based on DGL [[GitHub](https://github.com/BUPT-GAMMA/OpenHGNN)] [[Notes](https://mp.weixin.qq.com/s/hz7vD5giWIs-eD9cE7H96A)]
3. `HGT(Heterogeneous Graph Transformer)` Heterogeneous Graph Transformer (WWW 2020) [[GitHub](https://github.com/acbull/pyHGT)]

## GNN Explanability
Surveys, Summary and Tutorials:
1. Explainability in Graph Neural Networks: A Taxonomic Survey [[Paper](https://arxiv.org/pdf/2012.15445.pdf)] [[Notes](https://zhuanlan.zhihu.com/p/359533369)]
2. XGraph (Benchmark) [[Github](https://github.com/divelab/DIG/tree/main/dig/xgraph)]
3. Counterfactual Explanations in Explainable AI: A Tutorial (KDD 2021) [[Website](https://sites.google.com/view/kdd-2021-counterfactual)]
4. A Survey of Data-driven and Knowledge-aware eXplainable AI (TKDE 2021) 

General Papers:
1. `GNNExplainer` GNNExplainer: Generating Explanations for Graph Neural Networks (NeurIPS 2019)
2. On Explainability of Graph Neural Networks via Subgraph Explorations [[Paper](https://arxiv.org/pdf/2102.05152.pdf)] 🌟
> * Shapley value --> taxi sharing
3. `PGExplainer` Parameterized Explainer for Graph Neural Network (NeurIPS 2020) [[Paper](https://github.com/flyingdoog/PGExplainer)]

Related reading:
1. ReduNet: A White-box Deep Network from the Principle of Maximizing Rate Reduction [[Paper](https://arxiv.org/pdf/2105.10446.pdf)] [[Some discussion](https://mp.weixin.qq.com/s/sZjn5Q8IBu6JXziTBJVLTg)]
2. Evaluating XAI: A comparison of rule-based and example-based explanations [[Paper](https://www.sciencedirect.com/science/article/pii/S0004370220301533)]

## Spatial Temporal GNN

## GNN Applications

## GNN in Database Community
1. Efficient Streaming Subgraph Isomorphism with Graph Neural Networks (VLDB 2021) [[Paper](http://vldb.org/pvldb/vol14/p730-duong.pdf)]
2. Accelerating Large Scale Real-Time GNN Inference using Channel Pruning (VLDB 2021)
3. Grain: Improving Data Efficiency of Graph Neural Networks via Diversified Influence Maximization (VLDB 2021)
4. Large Graph Convolutional Network Training with GPU-Oriented Data Communication Architecture (VLDB 2021)
5. Multi-Modal Transportation Recommendation with Unified Route Representation Learning (VLDB 2021)
6. ICS-GNN: Lightweight Interactive Community Search via Graph Neural Network (VLDB 2021)

# Other Related Reading

1. Graph Embedding Techniques, Applications, and Performance: A Survey [[Paper](https://arxiv.org/pdf/1705.02801.pdf)]
2. Representation Learning on Graphs with Jumping Knowledge Networks [[Paper](http://proceedings.mlr.press/v80/xu18c/xu18c.pdf)]
3. Informed Machine Learning – A Taxonomy and Survey of Integrating Prior Knowledge into Learning Systems (TKDE 2021)

## Homepages of Talented People
1. Rex Ying [[Website](https://cs.stanford.edu/people/rexy/index.html)]
