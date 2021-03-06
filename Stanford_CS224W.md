## Lecture 1: Introduction; Machine Learning for Graphs
1. Different types of tasks:
* Node level: node classification
* Edge level: recommeder system
* Subgraph level: traffic prediction
* Graph level: drug discovery, physic simulation
2. Graph representation: matrix, edge list, adjacency list (Easier to work with if network is large and sparse)
3. Different types of graphs

## Lecture 2: Traditional Methods for ML on Graphs

Goal: Make predictions for a set of objects

Design choices:
* Features: d-dimensional vectors
* Objects: Nodes, edges, sets of nodes, entire, graphs
* Objective function: What task are we aiming to solve?

1. Node level task and features (Goal: Characterize the structure and position of a node in the network)
* Node centrality: 
> * Eigenvector centrality: A node is important if surrounded by important neighboring nodes. <img src="https://github.com/heathersherry/GNN/blob/main/figures/nodecentrality1.png" width="400"/>
> * Betweenness centrality: A node is important if it lies on many shortest paths between other nodes. <img src="https://github.com/heathersherry/GNN/blob/main/figures/nodecentrality2.png" width="400"/>
> * Closeness centrality: A node is important if it has small shortest path lengths to all other nodes. <img src="https://github.com/heathersherry/GNN/blob/main/figures/nodecentrality3.png" width="400"/>
* Node features:
> * Clustering coefficient: Measures how connected v's neighboring nodes are. <img src="https://github.com/heathersherry/GNN/blob/main/figures/nodefeature1.png" width="400"/>
> * Graphlets: Rooted connected non-isomorphic subgraphs. We use __graphlet degree vector (GDV)__ to count graphlets rooted at a given node. <img src="https://github.com/heathersherry/GNN/blob/main/figures/nodefeature2.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/nodefeature3.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/nodefeature4.png" width="400"/>
> 
2. Link level task and features (Goal: predict new links based on existing links, with two formulations: (1) Links missing at random, and (2) links over time)
* Link level features
> * Distance-based feature: Shortest-path distance between two nodes. <img src="https://github.com/heathersherry/GNN/blob/main/figures/linkfeature1.png" width="400"/>
> * Local neighborhood overlap: Captures # neighboring nodes shared between two nodes v1 and v2 (limitation: not global view). <img src="https://github.com/heathersherry/GNN/blob/main/figures/linkfeature2.png" width="400"/>
> * Global neighborhood overlap: Katz index, which counts the number of paths of all lengths between a given pair of nodes. <img src="https://github.com/heathersherry/GNN/blob/main/figures/linkfeature3.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/linkfeature4.png" width="400"/>

3. Graph level task and features (Goal: We want features that characterize the structure of an entire graph)
* Graph Kernels: Measure similarity between two graphs
> * Graphlet Kernel: graphlet feature, which counts the number of different graphlets in a graph (limitations: the counting is expensive)
> <img src="https://github.com/heathersherry/GNN/blob/main/figures/graphfeature1.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/graphfeature2.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/graphfeature3.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/graphfeature4.png" width="400"/>
> * Weisfeiler-Lehman Kernel: use neighborhood structure to iteratively enrich node vocabulary. ALgorithm: Color refinement, while the time complexity is linear to the # of egdes
> <img src="https://github.com/heathersherry/GNN/blob/main/figures/graphfeature5.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/graphfeature6.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/graphfeature7.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/graphfeature8.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/graphfeature9.png" width="400"/> 

## Lecture 3: Node Embeddings

Goal: graph representation learning, a way to learn node and graph embeddings for downstream tasks, without feature engineering.

1. Node embedding
* Encoder + Decoder Framework (unsupervised/self-supervised way of learning node embeddings, no node label, no node feature, just to preserve the network structure, task independent)
> * encoder: maps each node to a low-dimensional vector
> * decoder: based on node similarity
> * objective: maximize z_v^Tz_u for node pairs (u,v) that are similar
* Random walk approaches
> * (1) Run short fixed-length random walks starting from each node on the graph
> * (2) For each node u collect N(u), the multiset of nodes visited on random walks starting from u
> * (3) Optimize embeddings using Stochastic Gradient Descen
> * <img src="https://github.com/heathersherry/GNN/blob/main/figures/WX20210815-223519%402x.png" width="400"/>
* DeepWalk: fixed-length, unbiased random walks starting from each node.
* Node2vec: Biased 2nd-order Random Walk (DFS+BFS), better used on node classfication than link prediction.
2. Embedding Entire Graph
* Approach 1: Embed nodes and sum/avg them 
* Approach 2: Create super-node that spans the (sub) graph and then embed that node
* Approach 3: Anonymous Walk Embeddings
> * Idea 1: Sample the anon. walks and represent the graph as fraction of times each anon walk occurs
> * Idea 2: Embed anonymous walks, concatenate their embeddings to get a graph embedding
 
## Lecture 4: Graph as Matrix: Page Rank, Random Walk, and Embeddings

1. PageRank: The "Flow" Model
> * Measures importance of nodes in a graph using the link structure of the web
> * Models a random web surfer using the stochastic adjacency matrix M
> * PageRank solves r = Mr where r can be viewed as both the principle eigenvector of M and as the stationary distribution of a random walk over the graph

2. PageRank: The solution
* PageRank solves for r = Gr and can be efficiently computed by power iteration of the stochastic adjacency matrix (G)
* <img src="https://github.com/heathersherry/GNN/blob/main/figures/pagerank.png" width="400"/>
* Teleprots: solve the dead-ends and spider-traps problem
> * Spider-traps: With prob. b, follow a link at random, With prob. 1-b, jump to a random page, b = 0.8 or 0.9 in pratice
> * Dead-ends: Follow random teleport links with total probability 1.0 from dead-ends
> * <img src="https://github.com/heathersherry/GNN/blob/main/figures/teleports.png" width="400"/>

3. RWR and PPR
* <img src="https://github.com/heathersherry/GNN/blob/main/figures/pagerank_variants.png" width="400"/>

## Lecture 5: Message Passing and Node CLassification
Goal: Semi-supervised node classification

Approach: Collective Classification
* <img src="https://github.com/heathersherry/GNN/blob/main/figures/collectiveclassification.png" width="400"/>
Three Collective Classification Models:

1. Relational classification
* <img src="https://github.com/heathersherry/GNN/blob/main/figures/relationalclassification.png" width="400"/>
* Challenges: (1) Convergence is not guaranteed, (2) Model cannot use node feature information
2. Iterative classification
* <img src="https://github.com/heathersherry/GNN/blob/main/figures/iterativeclassification1.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/iterativeclassification2.png" width="400"/>
* Improvements: (1) Improve over collective classification to handle attribute/feature information, (2) Classify node i based on its features as well as labels of neighbors
3. Loopy Belief propagation
* <img src="https://github.com/heathersherry/GNN/blob/main/figures/loopypropagation.png" width="400"/>
* Advantages: Easy to program and parallel, can be apply to any graph model with any form of potentials (e.g., higher order)
* Challenges: Convergence not guaranteed (especially with many closed loops)

## Lecture 6: Graph Neural Networks
1. Basic of Deep Learning
* Machine learning as optimization (min loss); Gradient vector and Stochastic gradient vector (SGD); epoch, iteration, batch size; back-propagation; MLP.
* <img src="https://github.com/heathersherry/GNN/blob/main/figures/basic_dl.png" width="400"/>
* <img src="https://github.com/heathersherry/GNN/blob/main/figures/graphdl_4.png" width="400"/>
2. Deep Learning for Graphs
* Neighborhood aggregation: Average information from neighbors and apply a neural network
* <img src="https://github.com/heathersherry/GNN/blob/main/figures/graphdl_1.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/graphdl_2.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/graphdl_3.png" width="400"/>
* Unsupervised learning
> * No node label available. Use the graph structure as the supervision!
> * ???Similar??? nodes have similar embeddings. Node similarity can be based on random walk/Matrix factorization/Node proximity in the graph.
* Supervised learning
> * Directly train the model for a supervised task (e.g., node classification)
> * (1) Define a neighborhood aggregation function; (2) Define a loss function on the embeddings; (3) Train on a set of nodes, i.e., a batch of compute graphs; (4)Generate embeddings for nodes as needed (even for new nodes)!
3. GCN and GraphSAGE
(Why Prof said byebye before introducing GraphSAGE??????????????? Oh he talked about it in Lecture 7 later ????)

## Lecture 7: A General Perspective on GNNs
1. A General GNN Framework
* <img src="https://github.com/heathersherry/GNN/blob/main/figures/generalGNN_1.png" width="400"/>
2. A Single GNN Layer
* MSG (linear layer) + AGG (e.g., SUM/MAX/AVG)
* <img src="https://github.com/heathersherry/GNN/blob/main/figures/generalGNN_2.png" width="400"/>
* Classical GNN Layers:
> * GCN
> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GCN1.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GCN2.png" width="400"/>
> * GraphSAGE
> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GraphSAGE1.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GraphSAGE2.png" width="400"/>
> * GAT             
> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GAT1.png" width="400"/>  <img src="https://github.com/heathersherry/GNN/blob/main/figures/GAT2.png" width="400"/>  <img src="https://github.com/heathersherry/GNN/blob/main/figures/GAT3.png" width="400"/>  <img src="https://github.com/heathersherry/GNN/blob/main/figures/GAT4.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GAT5.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GAT6.png" width="400"/>        
> Mnay modern deep learning modules can be included into a GNN layer for better performance 
> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNpractise1.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNpractise2.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNpractise3.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNpractise4.png" width="400"/>  
3. Stacking Layers of a GNN
* <img src="https://github.com/heathersherry/GNN/blob/main/figures/stackingGNN1.png" width="400"/>
* Lesson 1: Be cautious when adding GNN layers
> * Solution 1: Increase the expressive power within each GNN layer
> * Solution 2: Add layers that do not pass messages
* Lesson 2: Add skip connections in GNNs (Intuition: Skip connections create a mixture of models)
4. Graph Manipulation in GNN
(Prof said byebye again ???? Ooooops he discussed this in Lecture 8 ????)

## Lecture 8: GNN Augmentation and Training
1. Graph Augmentation of GNNs
* Graph Feature augmentation
> * The input graph lacks features --> feature augmentation
> * <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNfeatureaug.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNfeatureaug1.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNfeatureaug2.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNfeatureaug3.png" width="400"/>
* Graph Structure augmentation
> * The graph is too sparse --> Add virtual nodes / edges 
> * <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNfeatureaug4.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNfeatureaug5.png" width="400"/>
> * The graph is too dense -->Sample neighbors when doing message passing
> * <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNfeatureaug6.png" width="400"/>
> * The graph is too large --> Sample subgraphs to compute embeddings

2. Prediction with GNNs
* GNN Training Pipeline (1): <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNprediction1.png" width="400"/> 
* Node Level Prediction
> * <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNprediction2.png" width="400"/> 
* Edge Level Prediction
> * <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNprediction3.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNprediction4.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNprediction5.png" width="400"/> 
* Graph Level Prediction
> * <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNprediction6.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNprediction7.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNprediction8.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNprediction9.png" width="400"/> 

3. Training GNNs
* GNN Training Pipeline (2): Where does ground-truth come from? Supervised labels and unsupervised labels
> * <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNtraining1.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNtraining2.png" width="400"/> 
* GNN Training Pipeline (3): How do we compute the final loss? Classification loss and regression loss
> * <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNloss1.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNloss2.png" width="400"/>
* GNN Training Pipeline (4): How do we measure the success of a GNN? Accuracy and ROC AUC
> * <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNevaluation1.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNevaluation2.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNevaluation3.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNevaluation4.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNevaluation5.png" width="400"/>
* GNN Training Pipeline (5): How do we split our dataset into train / validation / test set?
> * <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNsplit1.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNsplit2.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNsplit3.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNsplit4.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNsplit5.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/GNNsplit6.png" width="400"/>

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

## Lecture 12: Identifying and Counting Motifs in Networks
1. Subgraphs and Motifs
* Defining Subgraphs and Motifs
> * Subgraph Definition <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph1.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph2.png" width="400"/>
> * Graph Isomorphism <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph3.png" width="400"/>
> * Subgraph Isomorphism <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph4.png" width="400"/>
> * Network Motifs <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph5.png" width="400"/>
* Determining Motif Significance
> * Subgraph Frequency <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph6.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph7.png" width="400"/>
> * Motif Significance (Key idea): Subgraphs that occur in a real network much more often than in a random network have functional significance.
> * Random Graphs: <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph8.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph9.png" width="400"/>
> * Detecting Motifs: <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph10.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph11.png" width="400"/>

2. Neural Subgraph Representations
* Subgraph Representation
> * <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph12.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph13.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph14.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph15.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph16.png" width="400"/> 
* We design loss functions based on the order constraint. Order constraint specifies the ideal order embedding property that reflects subgraph relationships
> * <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph17.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph18.png" width="400"/>
* Training
> * <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph19.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph20.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph21.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph22.png" width="400"/>
3. Mining Frequent Subgraphs
* SPMiner Motivation <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph23.png" width="400"/>
* Overview: <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph24.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph25.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/subgraph26.png" width="400"/>


## Lecture 13: Community Detection in Networks
1. Network Communities
* Overview 
> <img src="https://github.com/heathersherry/GNN/blob/main/figures/community1.png" width="400"/>
* Modularity 
> <img src="https://github.com/heathersherry/GNN/blob/main/figures/community2.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/community3.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/community4.png" width="400"/>
2. Louvain Algorithm: A greedy algorihtm for community detection
* Overview
> <img src="https://github.com/heathersherry/GNN/blob/main/figures/community5.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/community6.png" width="400"/>
* Phase 1
> <img src="https://github.com/heathersherry/GNN/blob/main/figures/community7.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/community8.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/community9.png" width="400"/>
* Phase 2
> <img src="https://github.com/heathersherry/GNN/blob/main/figures/community10.png" width="400"/>
3. BigCALM: Detecting Overlapped Communities
* Overview <img src="https://github.com/heathersherry/GNN/blob/main/figures/community11.png" width="400"/>
* Step 1 <img src="https://github.com/heathersherry/GNN/blob/main/figures/community12.png" width="400"/>
* Step 2 <img src="https://github.com/heathersherry/GNN/blob/main/figures/community13.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/community14.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/community15.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/community16.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/community17.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/community18.png" width="400"/> 

## Lecture 14: Generative Models for Graphs
1. Properties of real-world graphs
* <img src="https://github.com/heathersherry/GNN/blob/main/figures/model1.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/model2.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/model3.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/model4.png" width="400"/>
2. Traditional graph generative models
* Erd??s-Renyi Random Graphs
> Basic Idea: * <img src="https://github.com/heathersherry/GNN/blob/main/figures/model5.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/model6.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/model7.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/model8.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/model9.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/model10.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/model11.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/model12.png" width="400"/>
> * Insightful conclusions from Erd??s-Renyi Random Graphs: <img src="https://github.com/heathersherry/GNN/blob/main/figures/model13.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/model14.png" width="400"/>
* The Small World Model
> * <img src="https://github.com/heathersherry/GNN/blob/main/figures/model15.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/model16.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/model17.png" width="400"/>
* Kronecker Graph Model
> * How can we think of network structure recursively? Intuition: Self-similarity
> * Simple Kronecker Graph Model: <img src="https://github.com/heathersherry/GNN/blob/main/figures/model18.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/model19.png" width="400"/>
> * Stochastic Kronecker Graph Model: <img src="https://github.com/heathersherry/GNN/blob/main/figures/model20.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/model21.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/model22.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/model23.png" width="400"/>
3. Deep graph generative models (Next Lecture)

## Lecture 15: Deep Generative Models for Graphs
1. Machine Learning for Graph Generation
* Realistic graph generation: Generate graphs that are similar to a given set of graphs
> * <img src="https://github.com/heathersherry/GNN/blob/main/figures/generation1.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/generation2.png" width="400"/>
2. GraphRNN: Realistic graph generation
* Pipeline:
> * <img src="https://github.com/heathersherry/GNN/blob/main/figures/generation2.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/generation3.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/generation4.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/generation5.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/generation6.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/generation7.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/generation8.png" width="400"/> 
* Summary:
> * Add a new node: We run Node RNN for a step, and use it output to initialize Edge RNN
> * Add new edges for the new node: We run Edge RNN to predict if the new node will connect to each of the previous node
> * Add another new node: We use the last hidden state of Edge RNN to run Node RNN for another step
> * Stop graph generation: If Edge RNN outputs EOS at step 1, we know no edges are connected to the new node. We stop the graph generation.
* Tracibility:
> * <img src="https://github.com/heathersherry/GNN/blob/main/figures/generation9.png" width="400"/> 
* Evaluation of two graphs:
> * Visual similarity
> * Graph statistics similarity: <img src="https://github.com/heathersherry/GNN/blob/main/figures/generation10.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/generation11.png" width="400"/> 
3. Applications of Deep Graph Generation Models
* Goal: <img src="https://github.com/heathersherry/GNN/blob/main/figures/generation12.png" width="400"/> 
* Drug Discovery
> * <img src="https://github.com/heathersherry/GNN/blob/main/figures/generation13.png" width="400"/>  <img src="https://github.com/heathersherry/GNN/blob/main/figures/generation14.png" width="400"/>  <img src="https://github.com/heathersherry/GNN/blob/main/figures/generation16.png" width="400"/>  <img src="https://github.com/heathersherry/GNN/blob/main/figures/generation15.png" width="400"/> 

## Lecture 16: Advanced Topics in GNNs
1. Limitations of GNN
* <img src="https://github.com/heathersherry/GNN/blob/main/figures/limit1.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/limit2.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/limit3.png" width="400"/>
* A na??ve solution: One-hot encoding, but not scalable (Need O(N) feature dimensions) and not inductive (cannot generalize to new nodes/graphs)
2. Position-Aware GNN
* <img src="https://github.com/heathersherry/GNN/blob/main/figures/limit4.png" width="400"/> 
* The number of nodes in the sets might exponentially decrease
3. Identity-Aware GNN
* <img src="https://github.com/heathersherry/GNN/blob/main/figures/limit5.png" width="400"/>  <img src="https://github.com/heathersherry/GNN/blob/main/figures/limit6.png" width="400"/>  <img src="https://github.com/heathersherry/GNN/blob/main/figures/limit7.png" width="400"/>  <img src="https://github.com/heathersherry/GNN/blob/main/figures/limit8.png" width="400"/> 
4. Robustness of GNN
* <img src="https://github.com/heathersherry/GNN/blob/main/figures/limit9.png" width="400"/>  <img src="https://github.com/heathersherry/GNN/blob/main/figures/limit10.png" width="400"/>  <img src="https://github.com/heathersherry/GNN/blob/main/figures/limit11.png" width="400"/>  <img src="https://github.com/heathersherry/GNN/blob/main/figures/limit12.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/limit13.png" width="400"/>  <img src="https://github.com/heathersherry/GNN/blob/main/figures/limit14.png" width="400"/> 

## Lecture 17: Scaling Up GNN to Large Graphs
1. Motivation
* <img src="https://github.com/heathersherry/GNN/blob/main/figures/scalability1.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/scalability2.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/scalability3.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/scalability4.png" width="400"/>
2. GraphSAGE: Neighbourhood Sampling
* <img src="https://github.com/heathersherry/GNN/blob/main/figures/scalability5.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/scalability6.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/scalability7.png" width="400"/>
3. Cluster-GCN
* <img src="https://github.com/heathersherry/GNN/blob/main/figures/scalability8.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/scalability9.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/scalability10.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/scalability11.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/scalability12.png" width="400"/> 
4. Simplified GCN
* <img src="https://github.com/heathersherry/GNN/blob/main/figures/scalability13.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/scalability14.png" width="400"/> 
