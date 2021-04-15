# An-algorithm-for-clustering-nodes-of-a-graph-in-a-synchronous-and-asynchronous-way

I will partition the nodes of an input graph (either directed or undirected) into clusters (communities) with the
help of the following algorithm. Let the neighbours of node $v$ be denoted by $v_1 , v_2 , \ldots, v_k$ , and let each node
also have a label $C_v$ that gives the community it belongs to. A node $v$ will determine its label based on the
labels of its neighbours: it will update it to the value that the maximum number of its neighbours have. If
there are multiple possible labels with the same maximum amount of neighbours, then the tie is broken in
a uniformly random way. Because labels will be updated iteratively, we define $C_v (t)$ as the label of a node
in iteration $t$. Nodes can be updated in either a synchronous or asynchronous way. Synchronous updating
means that the label of a node v in iteration t will depend on the labels of its neighbours in the previous
iteration: $$C_v(t) = f(C_{v_1}(t-1), C_{v_2}(t-1), \ldots, C_{v_k}(t-1).$$

However, this can lead to the oscillation of labels in certain neighbourhood structures. In the case
of asynchronous updates, the new values will be considered for neighbours whose label has already been
updated. Let $v_{i1} , v_{i2} , \ldots, $v_{im}$ denote the already updated $m$ neighbours of $v$, the asynchronous update is as
follows: $$C_v(t) = f(C_{v1}(t), C_{v2}(t), \ldots, C_{vm}(t), C_{v(m+1)}(t-1), \ldots, C_{vk}(t-1)).$$

The algorithm iterates until it can update any label. If no label updates happen in an iteration, the
algorithm terminates, and the current labels give the clusters (communities) where each node belongs. The
outline of the algorithm can be seen below:
  1. Initialize labels: For all $v \in V$, let $C_v(0) = v
  2. Set $t=1$
  3. Determine random update order for $V$
  4. For each $v \in V$ in the update order of $3$., determine $C_v(t)$
  5. If no label has been updated, terminate. Otherwise,  $t=t +1$ and go to 3.

Except implementing the algorithm I will aslo perform a $k$-means and a hierarchical clustering of the nodes of the graph (using the number of clusters I got from the algorithm above). The shortest path will be used as a distance between nodes, I will also try different linkage methods and centroids. 
