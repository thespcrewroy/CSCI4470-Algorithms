# Disjoint Set Data Structures (DSDS)

- A collection of **non-overlapping (disjoint) sets**
- Each element belongs to **exactly one set**

## Definition

Let:

S = { S<sub>1</sub>, S<sub>2</sub>, ..., S<sub>n</sub> }

- Each S<sub>i</sub> is a subset
- The sets are **disjoint**: S<sub>i</sub> &cap; S<sub>j</sub> = &empty;   for i &ne; j
- No two sets share any common elements  
- Every set is **independent**

## Example

Q) S = { S₁, S₂ }

- S₁ = {2, 4, 7}   (representative = 2)
- S₂ = {3, 8, 5}   (representative = 3)
- S<sub>i</sub> &cap; S<sub>j</sub> = &empty;: No common elements, so sets are disjoint

## Applications
- Connected components
- Union-Find algorithms
- Graph cycle detection

## Implementation
- **Find(x)**: find which set x belongs to
- **Union(x, y)*#: merge two sets