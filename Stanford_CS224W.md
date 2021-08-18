### Lecture 1: Introduction; Machine Learning for Graphs
1. Different types of tasks:
* Node level: node classification
* Edge level: recommeder system
* Subgraph level: traffic prediction
* Graph level: drug discovery, physic simulation
2. Graph representation: matrix, edge list, adjacency list (Easier to work with if network is large and sparse)
3. Different types of graphs

### Lecture 2: Traditional Methods for ML on Graphs

Goal: Make predictions for a set of objects

Design choices:
* Features: d-dimensional vectors
* Objects: Nodes, edges, sets of nodes, entire, graphs
* Objective function: What task are we aiming to solve?

1. Node level task and features (Goal: Characterize the structure and position of a node in the network)
* Node centrality: 
> * Eigenvector centrality: A node is important if surrounded by important neighboring nodes.
> * Betweenness centrality: A node is important if it lies on many shortest paths between other nodes.
> * Closeness centrality: A node is important if it has small shortest path lengths to all other nodes.
* Node features:
> * Clustering coefficient: Measures how connected v's neighboring nodes are.
> * Graphlets: Rooted connected non-isomorphic subgraphs. We use __graphlet degree vector (GDV)__ to count graphlets rooted at a given node.
> 
2. Link level task and features (Goal: predict new links based on existing links, with two formulations: (1) Links missing at random, and (2) links over time)
* Link level features
> * Distance-based feature: Shortest-path distance between two nodes
> * Local neighborhood overlap: Captures # neighboring nodes shared between two nodes v1 and v2 (limitation: not global view)
> * Global neighborhood overlap: Katz index, which counts the number of paths of all lengths between a given pair of nodes.
3. Graph level task and features (Goal: We want features that characterize the structure of an entire graph)
* Graph Kernels: Measure similarity between two graphs
> * Graphlet Kernel: graphlet feature, which counts the number of different graphlets in a graph (limitations: the counting is expensive)
> * Weisfeiler-Lehman Kernel: use neighborhood structure to iteratively enrich node vocabulary. ALgorithm: Color refinement, while the time complexity is linear to the # of egdes

### Lecture 3: Node Embeddings

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
 
### Lecture 4: Graph as Matrix: Page Rank, Random Walk, and Embeddings

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

### Lecture 5: Message Passing and Node CLassification
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

### Lecture 6
