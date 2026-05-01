# Prim's Greedy Algorithm

## Notes: Definition
- Greedy Algorithm: pick the cheapest edge that connects a vertex inside the tree to a vertex outside the tree.
- Take the sum of all the edges you added to determine the cost
- Optimal for dense graphs where E &#8494; V<sup>2</sup>
- Utilizes a minimum prioirity queue in its implementation

```
Time Complexity: O(Elog(V)) 
```

## Notes: Prim's Time Complexity Analysis

```
(V + E)log(V)
V + E ~ E (for dense graphs)
O(Elog(V))
```

**Complete Graph Time Complexity: O(Elog(V))**

## Notes: Implementation Example

- Create a minimum priority queue with all the vertices
- You are using the key parameter to create the heap
- If the key value is bigger than weight, then update the **key** to minimize it

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/primwalk2.png" alt="Prim Walkthrough" width="500"  />
</p>

**Initialization**
- b.key = &alpha;
- b.&pi; = NIL
- h.key = &alpha;
- h.&pi; = NIL

**a.key = 0**
<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/minqueue1.png" alt="Min Prioirty Queue 1" height="150" width="150"  />
</p>

**dequeue(a)**
- b.key = &alpha;
- h.key = &alpha;
- w(a,b) = 4
- w(a,h) = 8
- b.key = 4
- h.key = 8

**b.key = 4**
<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/minqueue2.png" alt="Min Prioirty Queue 2" height="150" width="150"  />
</p

**dequeue(b)**
- h.key = 8
- c.key = &alpha;
- w(b, h) = 11
- w(b, c) = 8
- h.key = 8
- c.key = 8

**c.key = 8**
<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/heap3.png" alt="Min Priority Queue 3" height="150" width="150"  />
</p>

**dequeue(c)**
- i.key = &infin;
- f.key = &infin;
- d.key = &infin;
- w(c, i) = 2
- w(c, f) = 4
- w(c, d) = 7
- i.key = 2
- f.key = 4
- d.key = 7

**i.key = 2**
<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/heap4.png" alt="Min Priority Queue 4" height="150" width="150"  />
</p>
  
**Current MST (Keep Going)**
<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/currenttree.png" alt="Current MST" height="250" width="300"  />
</p>
  

## Homework: Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/hw4-6.png" alt="Prim's Algo Example"  />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/hw4-6-2.png" alt="Prim's Algo Example"  />
</p>