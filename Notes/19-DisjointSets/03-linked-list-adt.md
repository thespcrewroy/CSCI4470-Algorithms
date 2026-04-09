# Linked List Disjoint Set


## Notes: Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/linkedlist.png" alt="Linked List Disjoint Set" width="800" />
</p>

There are a lot of pointers.

```
Time Complexity: O(1)
```

### Make_Set(A)

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/makelinked.png" alt="Make Linked List Disjoint Set" width="800" />
</p>

```
Time Complexity: O(1)
```

### Find_Set(B)

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/findlinked.png" alt="Find Linked List Disjoint Set" width="800" />
</p>

```
Time Complexity: O(1)
```

### Union(S<sub>1</sub>, S<sub>2</sub>)

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/unionlinked.png" alt="Union Linked List Disjoint Set" width="800" />
</p>

Append the smaller set into the bigger set.

```
Time Complexity: O(n)
- Append: O(1)
- Connect 'n' pointers to representative: O(n)
```