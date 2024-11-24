[[Greedy method]]

playlist https://youtube.com/playlist?list=PLfFeAJ-vQopt_S5XlayyvDFL_mi2pGJE3&si=pHqXKGQOLlHpIGDo
### Greedy Algorithms: Definition

Greedy algorithms are a class of algorithms that make locally optimal choices at each stage with the hope of finding a global optimum. The fundamental principle behind greedy algorithms is to choose the best option available at the moment, without considering the larger problem as a whole.

### Key Characteristics

1. **Locally Optimal Choice**: At each step, a greedy algorithm makes a choice that looks best at the moment, aiming to optimize some criterion (e.g., cost, distance, profit).

2. **Feasibility**: Each choice made must be feasible, meaning it must satisfy the problem's constraints.

3. **Irrevocability**: Once a choice is made, it cannot be undone; future choices are based on this decision.

4. **Global Optimum**: Greedy algorithms do not always produce a global optimum solution; however, they can be efficient and produce acceptable solutions for many problems.

### Common Greedy Algorithms

1. **Activity Selection Problem**: Selecting the maximum number of activities that don't overlap.
  
2. **Kruskal’s and Prim’s Algorithms**: Finding the minimum spanning tree in a graph.

3. **Dijkstra’s Algorithm**: Finding the shortest path in a weighted graph.

4. **Huffman Coding**: Creating an optimal prefix code based on character frequencies.

### Applications
Greedy algorithms are widely used in optimization problems where the solution can be built incrementally. They are particularly useful in scenarios where a global optimum can be derived from local optima.

### Conclusion
While greedy algorithms are powerful and efficient for certain types of problems, it's important to analyze whether a greedy approach is appropriate for a given situation. In cases where a global optimum is required, other methods such as dynamic programming or backtracking may be necessary.

![[Greedy Algorithms - GeeksforGeeks.pdf]]