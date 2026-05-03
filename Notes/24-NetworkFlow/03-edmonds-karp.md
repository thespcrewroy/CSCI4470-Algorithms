# Edmonds-Karp Algorithm

- Similar to the ford-fulkerson algorithm
- Not naive like ford-fulkerson
- Tells you how to select the augmenting path to do the least possible iterations
- Utilizes a BFS-based algorithm as its implementation to find the correct augmented path
- By using BFS to find the augmenting path, the max number of times an edge can become critical is `V/2 - 1`