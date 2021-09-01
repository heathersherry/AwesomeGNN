## Lecture 9: How Expressive are GNNs?
1. GNN examples
* <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNexpress1.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNexpress2.png" width="400"/>
2. GNN Computation Graphs
* Most expressive GNN should map subtrees to the node embeddings injectively.
* <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNexpress3.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNexpress4.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNexpress5.png" width="400"/>
3. Designing the most powerful GNN
* Motivation: 
> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNexpress6.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNexpress7.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNexpress8.png" width="400"/>
* GIN (Graph Isomophysm Network)
> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNexpress9.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNexpress10.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNexpress11.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNexpress12.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNexpress13.png" width="400"/>
* GIN and WL Graph Kernel (colore refinement algorithm in Lec 2)
> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNexpress14.png" width="400"/>
* Improving...
> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNexpress15.png" width="400"/>

## Lecture 10: Heterogenous Graph and Knowledge Graph Embedding
1. Heterogenous Graph and RGCN
* RGCN Definition
> <img src="https://github.com/heathersherry/GNN/blob/main/figures/RGCN1.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/RGCN2.png" width="400"/>
* Scalability <img src="https://github.com/heathersherry/GNN/blob/main/figures/RGCN3.png" width="400"/>
> * Block Diagonal Matrices <img src="https://github.com/heathersherry/GNN/blob/main/figures/RGCN4.png" width="400"/>
> * Basic Learning (aka Dictionary Learning, B=10~100) <img src="https://github.com/heathersherry/GNN/blob/main/figures/RGCN5.png" width="400"/>
* Examples
> * Node Classfication <img src="https://github.com/heathersherry/GNN/blob/main/figures/RGCN6.png" width="400"/>
> * Link Prediction <img src="https://github.com/heathersherry/GNN/blob/main/figures/RGCN7.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/RGCN8.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/RGCN9.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/RGCN10.png" width="400"/>

2. Knowledge Graph: KG Completion with Embeddings
* Given an enormous KG, For a given (head, relation), we predict missing tails. (Note this is slightly different from link prediction task)
* KG Representation <img src="https://github.com/heathersherry/GNN/blob/main/figures/KGE1.png" width="400"/>
* TransE <img src="https://github.com/heathersherry/GNN/blob/main/figures/KGE2.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/KGE3.png" width="400"/>
* TransR <img src="https://github.com/heathersherry/GNN/blob/main/figures/KGE4.png" width="400"/>
* DistMul <img src="https://github.com/heathersherry/GNN/blob/main/figures/KGE5.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/KGE6.png" width="400"/>
* ComplEx <img src="https://github.com/heathersherry/GNN/blob/main/figures/KGE7.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/KGE8.png" width="400"/>
* Summary <img src="https://github.com/heathersherry/GNN/blob/main/figures/KGEsummary1.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/KGEsummary2.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/KGEsummary3.png" width="400"/> 

## Lecture 11: Reasoning in Knowledge Graphs
1. Answering Predictive Queries in KGs
* KG queries
> <img src="https://github.com/heathersherry/GNN/blob/main/figures/KGreasoning1.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/KGreasoning2.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/KGreasoning3.png" width="400"/>
* Traversing KG to answer the queries <img src="https://github.com/heathersherry/GNN/blob/main/figures/KGreasoning4.png" width="400"/>
> Not a good solution... <img src="https://github.com/heathersherry/GNN/blob/main/figures/KGreasoning6.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/KGreasoning5.png" width="400"/>
> Predictive Queries (the middle node could be arbitrary) <img src="https://github.com/heathersherry/GNN/blob/main/figures/KGreasoning7.png" width="400"/>
* Path queries
> <img src="https://github.com/heathersherry/GNN/blob/main/figures/KGQA1.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/KGQA2.png" width="400"/>
* Conjunctive queries
> * Cannot use TransE. Reason: <img src="https://github.com/heathersherry/GNN/blob/main/figures/KGQA3.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/KGQA4.png" width="400"/>

2. Query2Box: Reasoning Over KGs Using Box Embedding
* Box Embedding Definition: 
> <img src="https://github.com/heathersherry/GNN/blob/main/figures/Box1.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/Box2.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/Box3.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/Box4.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/Box5.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/Box6.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/Box7.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/Box8.png" width="400"/>
* Embedding AND-OR Queries
> <img src="https://github.com/heathersherry/GNN/blob/main/figures/Box10.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/Box11.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/Box12.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/Box13.png" width="400"/>
* Training
> * Predefined templates
> * <img src="https://github.com/heathersherry/GNN/blob/main/figures/Box15.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/Box16.png" width="400"/>

