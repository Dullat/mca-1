https://youtu.be/pgNE06YbDZ8?si=kwDDlR-tzDTfd9NK

The **All-Pairs Shortest Path (APSP)** problem is a classical problem in graph theory where the objective is to find the shortest paths between all pairs of nodes in a graph. This means you want to compute the shortest path from every node \( u \) to every other node \( v \), and store these distances in a matrix or some similar structure.

### **Problem Definition**
Given a weighted directed graph \( G = (V, E) \), where \( V \) is the set of vertices and \( E \) is the set of edges, the goal is to compute the shortest distance from each vertex \( u \) to each other vertex \( v \). 

### **Key Algorithms for APSP**

There are two main algorithms to solve the All-Pairs Shortest Path problem:

#### 1. **Floyd-Warshall Algorithm** (Dynamic Programming)
   - **Time Complexity**: \( O(V^3) \)
   - **Space Complexity**: \( O(V^2) \)

#### 2. **Johnson's Algorithm** (Optimized for sparse graphs)
   - **Time Complexity**: \( O(V^2 \log V + VE) \) with Dijkstra's algorithm for each vertex
   - **Space Complexity**: \( O(V^2) \)

We'll focus on the **Floyd-Warshall algorithm**, as it is simpler and directly solves the APSP problem in \( O(V^3) \) time.

### **1. Floyd-Warshall Algorithm**

The **Floyd-Warshall algorithm** is a dynamic programming-based approach that computes the shortest paths between all pairs of vertices in a graph. It iteratively "relaxes" edges, checking whether the current shortest known path between two vertices can be improved by passing through another vertex.

#### **Steps of the Floyd-Warshall Algorithm:**

1. **Initialization**:
   - Create a distance matrix \( dist[][] \), where \( dist[i][j] \) will represent the shortest distance from vertex \( i \) to vertex \( j \).
   - Initialize the matrix:
     - \( dist[i][j] = \text{weight of edge} (i, j) \) if there is an edge from \( i \) to \( j \).
     - \( dist[i][i] = 0 \) (distance from any vertex to itself is zero).
     - \( dist[i][j] = \infty \) (for all other pairs \( i \neq j \), if there is no direct edge between them).
   
2. **Dynamic Programming**:
   - For each vertex \( k \) (consider it as an intermediate vertex), update the matrix by checking whether the path from \( i \) to \( j \) through \( k \) is shorter than the direct path from \( i \) to \( j \).
   - The update rule is:
     \[
     dist[i][j] = \min(dist[i][j], dist[i][k] + dist[k][j])
     \]
     This checks if the shortest path from \( i \) to \( j \) can be improved by passing through vertex \( k \).

3. **Repeat for all intermediate vertices**: 
   - The algorithm will run for each vertex \( k \) (as an intermediate vertex) and update the shortest path matrix for all pairs \( (i, j) \).
   
4. **Result**:
   - After \( V \) iterations (one for each vertex as an intermediate vertex), the matrix `dist` will contain the shortest distances between all pairs of nodes.

### **Floyd-Warshall Algorithm - Pseudocode**

```python
def floyd_warshall(graph):
    # V is the number of vertices
    V = len(graph)
    
    # Initialize the distance matrix with the graph's edge weights
    dist = [[float('inf')] * V for _ in range(V)]
    
    for i in range(V):
        dist[i][i] = 0  # Distance from a node to itself is zero
        
    for u in range(V):
        for v, weight in graph[u]:
            dist[u][v] = weight  # Set direct edge weights
    
    # Floyd-Warshall: Update the distance matrix
    for k in range(V):
        for i in range(V):
            for j in range(V):
                # Check if the path through k is shorter
                if dist[i][j] > dist[i][k] + dist[k][j]:
                    dist[i][j] = dist[i][k] + dist[k][j]
    
    return dist
```

### **Explanation**:
- **Step 1**: The graph is represented as an adjacency list (or matrix). For each pair of nodes, the matrix is initialized to store the direct edge weight (or infinity if no edge exists).
- **Step 2**: The three nested loops are used to update the shortest path distances. The outermost loop iterates over each intermediate vertex \( k \), and the two inner loops iterate over all pairs \( (i, j) \) of vertices.
- The distance from \( i \) to \( j \) is updated to be the minimum of its current value or the path that goes through \( k \), i.e., \( dist[i][j] = \min(dist[i][j], dist[i][k] + dist[k][j]) \).

### **Example**:
Consider the following graph:

```
Vertices: A, B, C
Edges: 
    A → B = 2
    A → C = 1
    B → C = 3
    C → A = 4
```

We initialize the distance matrix:

|    | A  | B  | C  |
|----|----|----|----|
| A  | 0  | 2  | 1  |
| B  | ∞  | 0  | 3  |
| C  | 4  | ∞  | 0  |

After applying the Floyd-Warshall algorithm:

1. Using **A** as an intermediate vertex, we find that \( dist[C][B] = dist[C][A] + dist[A][B] = 4 + 2 = 6 \).
2. The final distance matrix would be:

|    | A  | B  | C  |
|----|----|----|----|
| A  | 0  | 2  | 1  |
| B  | 5  | 0  | 3  |
| C  | 4  | 6  | 0  |

Thus, the shortest path between all pairs is computed.

### **Time and Space Complexity**:
- **Time Complexity**: The algorithm consists of three nested loops, each iterating \( V \) times (for each vertex). Therefore, the time complexity is \( O(V^3) \).
- **Space Complexity**: The space complexity is \( O(V^2) \) because we store the shortest path distances in a 2D matrix of size \( V \times V \).

### **Applications of APSP**:
1. **Network Routing**: To find the shortest paths between all pairs of routers or network nodes.
2. **All-Pairs Distance Calculation**: In applications like social network analysis, where you may want to know the distance between all pairs of individuals or entities.
3. **Graph Analysis**: For problems that require knowing the shortest path between every pair of vertices, such as in flow problems, pathfinding, and optimizations.
4. **Data Mining**: In clustering problems, where distances between all pairs of data points need to be calculated.

### **Limitations**:
- **Time Complexity**: \( O(V^3) \) is considered too slow for very large graphs (e.g., in scenarios where \( V \) is large, like in real-time applications or massive networks). In such cases, **Johnson's Algorithm** (which uses **Dijkstra’s algorithm**) can be more efficient.

### **Conclusion**:
The **Floyd-Warshall algorithm** is an elegant and simple approach to solve the All-Pairs Shortest Path problem. While its \( O(V^3) \) time complexity makes it practical for smaller graphs, it may not be suitable for large-scale graphs. However, it is an essential algorithm in the study of graph theory and has broad applications in areas where you need to find the shortest paths between all pairs of nodes.