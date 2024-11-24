# Dijkstra's algorithm

https://youtu.be/Gd92jSu_cZk?si=MS4Rt2pGikTqVFkc

#### graph search algorithm

The Single Source Shortest Path (SSSP) problem is a fundamental problem in graph theory, aiming to find the shortest path from a designated source vertex to all other vertices in a weighted graph. The graph may be directed or undirected, and the edge weights can be arbitrary (positive, negative, or zero).

## Dijkstra’s Algorithm

One of the most well-known algorithms for solving the SSSP problem is Dijkstra’s algorithm, developed by Edsger W. Dijkstra in 1959. It is a greedy algorithm that works by maintaining a priority queue of vertices, where the priority of each vertex is its minimum distance from the source vertex. The algorithm iteratively extracts the vertex with the minimum priority from the queue and updates the distances of its neighbors.

Dijkstra’s algorithm has a time complexity of O(|E|log|V|) for directed graphs and O(|E|+|V|log|V|) for undirected graphs, where |E| is the number of edges and |V| is the number of vertices. It is guaranteed to find the shortest path to all vertices from the source vertex, provided that the edge weights are non-negative.