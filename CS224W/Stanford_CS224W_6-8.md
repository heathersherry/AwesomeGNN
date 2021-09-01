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
> * “Similar” nodes have similar embeddings. Node similarity can be based on random walk/Matrix factorization/Node proximity in the graph.
* Supervised learning
> * Directly train the model for a supervised task (e.g., node classification)
> * (1) Define a neighborhood aggregation function; (2) Define a loss function on the embeddings; (3) Train on a set of nodes, i.e., a batch of compute graphs; (4)Generate embeddings for nodes as needed (even for new nodes)!
3. GCN and GraphSAGE
(Why Prof said byebye before introducing GraphSAGE???😭😭😭 Oh he talked about it in Lecture 7 later 🥰)

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
(Prof said byebye again 😭 Ooooops he discussed this in Lecture 8 😆)

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

