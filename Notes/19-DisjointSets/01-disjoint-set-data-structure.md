# Disjoint Set Data Structures (DSDS)

- A collection of **non-overlapping (disjoint) sets**
- Each element belongs to **exactly one set**
- Use-Case: the cheapest way of finding out cycles

## Slides: Definition

Let:

S = { S<sub>1</sub>, S<sub>2</sub>, ..., S<sub>n</sub> }

- Each S<sub>i</sub> is a subset
- The sets are **disjoint**: S<sub>i</sub> &cap; S<sub>j</sub> = &empty;   for i &ne; j
- No two sets share any common elements  
- Every set is **independent**

## Notes: Example

Q) S = { S₁, S₂ }

- S₁ = {2, 4, 7}   (representative = 2)
- S₂ = {3, 8, 5}   (representative = 3)
- S<sub>i</sub> &cap; S<sub>j</sub> = &empty;: No common elements, so sets are disjoint

## Notes: Applications
- Connected components
- Union-Find algorithms
- Graph cycle detection

## Slides: 3 Operation Implementation
- **Make_Set(x)**: creates a set (S = {x})
- **Find_Set(x)**: returns a pointer to the representative for the set containing x
- **Union(x, y)**: merge set containing x with set containing y

## Notes: Cost Analysis

```
Time Complexity: O(m α (n))
```

- m: total number of MakeSet, FindSet, and Union operations.
- n: total number of MakeSet operations
- &alpha;(n): a constant or slow growing f(n)
- 'm' is linear in number of operations, and thus, making it better than BFS/DFS
