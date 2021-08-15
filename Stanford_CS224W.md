__Lecture 1: Introduction; Machine Learning for Graphs__
1. Different types of tasks:
* Node level: node classification
* Edge level: recommeder system
* Subgraph level: traffic prediction
* Graph level: drug discovery, physic simulation
2. Graph representation: matrix, edge list, adjacency list (Easier to work with if network is large and sparse)
3. Different types of graphs

__Lecture 2: Traditional Methods for ML on Graphs__

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

__Lecture 3: Node Embedding___

Goal: Efficient task-independent feature learning for machine learning with graphs

