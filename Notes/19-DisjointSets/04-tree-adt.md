# Tree Disjoint Set

**Preffered over linked list implementation**

## Notes: Example
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/tree.png" alt="Tree Disjoint Set" height="800" width="300" />
</p>

### Make_Set(A)

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/makea.png" alt="Find Linked List Disjoint Set" width="500" />
</p>


```
Time Complexity: O(1)
```

### Find_Set(D)

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/findd.png" alt="Find Linked List Disjoint Set" width="500" />
</p>

```
Time Complexity: O(1)
```

### Union(S<sub>1</sub>, S<sub>2</sub>)

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/unions.png" alt="Union of Trees" height="600" width="300" />
</p>

- Merge the smaller set into the bigger set
- Link the representative of the smaller with the representative of the bigger
- The representative of the bigger set takes over in the new connected set
- All you are doing is changing one pointer

```
Time Complexity: O(1)
```

## Notes: Path Compression

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/pathcompression.png" alt="Path Compression" width="500" />
</p>


- We know that the representative is A at all times as we travel along the tree
- So we can reduce the size of the path
- Advantage: returns find_set(A) in constant time
- Tradeoff: one time cost of compression in exchange for constant search time

## Notes: Rank

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/rank.png" alt="Path Compression" width="500" />
</p>

- The height of the tree
- Needed for the Union(S<sub>1</sub>, S<sub>2</sub>) operation