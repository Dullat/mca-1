![](https://youtu.be/pcKY4hjDrxk?si=lzQ9cGxe_GxScnjY)

https://www.javatpoint.com/depth-first-search-algorithm

Traversing a graph involves visiting all the vertices and edges systematically. The two primary methods of graph traversal are **Breadth-First Search (BFS)** and **Depth-First Search (DFS)**. Below are detailed explanations of both methods, along with pseudocode.

### 1. Breadth-First Search (BFS)

**Description**: BFS explores the graph level by level, starting from a source vertex and visiting all its neighbors before moving on to the next level.

**Key Features**:
- Uses a queue to keep track of vertices to visit next.
- Ideal for finding the shortest path in unweighted graphs.

**Pseudocode**:
```plaintext
BFS(Graph, start_vertex):
    Create a queue Q
    Create a set visited to keep track of visited vertices

    Enqueue start_vertex into Q
    Mark start_vertex as visited

    While Q is not empty:
        current_vertex = Dequeue Q
        Print current_vertex
        
        For each neighbor in Graph.adjacencyList[current_vertex]:
            If neighbor is not in visited:
                Enqueue neighbor into Q
                Mark neighbor as visited
```

### 2. Depth-First Search (DFS)

**Description**: DFS explores as far as possible along each branch before backtracking. It can be implemented either using recursion or a stack.

**Key Features**:
- Uses a stack (either explicitly or via recursion) to keep track of vertices.
- Can be used for topological sorting, finding connected components, and cycle detection.

**Pseudocode** (Recursive):
```plaintext
DFS(Graph, vertex, visited):
    Mark vertex as visited
    Print vertex

    For each neighbor in Graph.adjacencyList[vertex]:
        If neighbor is not visited:
            DFS(Graph, neighbor, visited)

DFS_Traversal(Graph, start_vertex):
    Create a set visited
    DFS(Graph, start_vertex, visited)
```

**Pseudocode** (Iterative):
```plaintext
DFS_Iterative(Graph, start_vertex):
    Create a stack S
    Create a set visited

    Push start_vertex onto S
    While S is not empty:
        current_vertex = Pop S
        
        If current_vertex is not in visited:
            Mark current_vertex as visited
            Print current_vertex
            
            For each neighbor in Graph.adjacencyList[current_vertex]:
                If neighbor is not in visited:
                    Push neighbor onto S
```

### Key Differences Between BFS and DFS

- **Order of Traversal**:
  - BFS explores neighbors first before going deeper, while DFS goes deep before exploring neighbors.
  
- **Data Structure Used**:
  - BFS uses a queue, while DFS uses a stack (or recursion).

- **Applications**:
  - BFS is useful for finding the shortest path in unweighted graphs, while DFS is often used for topological sorting, finding strongly connected components, and cycle detection.

### Summary

Graph traversal is fundamental for various applications in computer science, including searching, pathfinding, and analyzing structures. Understanding both BFS and DFS allows you to choose the appropriate method based on the specific requirements of the problem you are solving.