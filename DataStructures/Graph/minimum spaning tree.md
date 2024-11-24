A **Minimum Spanning Tree (MST)** is a subset of the edges of a connected, undirected graph that connects all the vertices together without any cycles and with the minimum possible total edge weight. Understanding MSTs is crucial in graph theory, computer science, and various applications such as network design, clustering, and more.

![](https://youtu.be/U1qDhdi5XJU?si=MS4FLyQSgH05rRaR)

![](https://youtu.be/4ZlRH0eK-qQ?si=HkueQ-q5XTeWCrRP)
### Key Concepts

1. **Graph Representation**:
   - A graph is represented as \( G = (V, E) \), where \( V \) is a set of vertices (nodes) and \( E \) is a set of edges (connections between nodes).
   - Each edge has a weight (cost), which can represent distance, cost, or any measurable quantity.

2. **Spanning Tree**:
   - A spanning tree is a subgraph that includes all vertices of the original graph and is connected without any cycles. It has exactly \( V - 1 \) edges if there are \( V \) vertices.

3. **Minimum Spanning Tree**:
   - An MST is a spanning tree with the minimum total edge weight among all possible spanning trees.

### Properties of Minimum Spanning Trees

- **Uniqueness**: If all edge weights are distinct, there is a unique MST.
- **Cycle Property**: In any cycle, if the weight of an edge is the largest, that edge cannot be part of the MST.
- **Cut Property**: For any cut in the graph, the minimum weight edge that crosses the cut must be part of the MST.

### Algorithms to Find MST

There are two popular algorithms to find the Minimum Spanning Tree:

1. **Kruskal's Algorithm**:
   - **Step 1**: Sort all edges in non-decreasing order of their weight.
   - **Step 2**: Start with an empty tree and add edges to the tree one by one. Always add the smallest edge that does not form a cycle.
   - **Step 3**: Repeat until you have \( V - 1 \) edges in the tree.

   **Data Structures**:
   - Uses Union-Find (Disjoint Set Union, DSU) to manage cycles.

   **Time Complexity**: \( O(E \log E) \) or \( O(E \log V) \) depending on the sorting method.

2. **Prim's Algorithm**:
   - **Step 1**: Start with a single vertex (arbitrarily chosen).
   - **Step 2**: Grow the spanning tree by adding the smallest edge from the tree to a vertex outside the tree.
   - **Step 3**: Repeat until all vertices are included.

   **Data Structures**:
   - Can use a priority queue (min-heap) to efficiently select the smallest edge.

   **Time Complexity**: \( O(E \log V) \) with a binary heap; \( O(V^2) \) with an adjacency matrix.

### Example

Consider a graph with vertices \( A, B, C, D \) and edges with weights:

- \( A - B: 1 \)
- \( A - C: 3 \)
- \( B - C: 2 \)
- \( B - D: 4 \)
- \( C - D: 5 \)

**Using Kruskal's Algorithm**:
1. Sort edges: \( A-B (1), B-C (2), A-C (3), B-D (4), C-D (5) \)
2. Start with an empty set.
3. Add \( A-B \) (1), then \( B-C \) (2), and finally \( A-C \) (3). Stop adding when we have 3 edges.
4. MST is \( A-B, B-C, A-C \) with total weight \( 1 + 2 + 3 = 6 \).

**Using Prim's Algorithm** (starting at A):
1. Start with \( A \), edges: \( A-B (1), A-C (3) \).
2. Choose \( A-B \) (1).
3. Now consider edges \( B-C (2), B-D (4) \) and choose \( B-C (2) \).
4. Now consider \( B-D (4), C-D (5) \) and choose \( B-D (4) \).
5. MST is \( A-B, B-C, B-D \) with total weight \( 1 + 2 + 4 = 7 \).

### Applications of MST

- **Network Design**: Connecting network nodes with minimum cost.
- **Clustering**: Grouping data points by their distances.
- **Approximation Algorithms**: Used in algorithms for NP-hard problems like the Traveling Salesman Problem.

### Conclusion

Understanding MSTs, their properties, and the algorithms to compute them is essential for solving many practical problems in computer science and engineering. Make sure to practice problems using both Kruskal's and Prim's algorithms to reinforce your understanding. Good luck with your exam preparation!

