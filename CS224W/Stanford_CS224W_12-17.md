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
* Erdös-Renyi Random Graphs
> Basic Idea: * <img src="https://github.com/heathersherry/GNN/blob/main/figures/model5.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/model6.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/model7.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/model8.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/model9.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/model10.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/model11.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/model12.png" width="400"/>
> * Insightful conclusions from Erdös-Renyi Random Graphs: <img src="https://github.com/heathersherry/GNN/blob/main/figures/model13.png" width="400"/> <img src="https://github.com/heathersherry/GNN/blob/main/figures/model14.png" width="400"/>
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
* A naïve solution: One-hot encoding, but not scalable (Need O(N) feature dimensions) and not inductive (cannot generalize to new nodes/graphs)
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
