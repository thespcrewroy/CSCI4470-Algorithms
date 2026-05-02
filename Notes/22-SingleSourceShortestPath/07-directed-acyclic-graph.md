# DAG Algorithm

- Applies only to directed acyclic graphs, so it cannot have a negative cycle
- Not all graphs in the real world fit the DAG definition (disadvantage)
  - PERT Charts are one application
- Negative edge wieghts are allowed (advantage)
- Utilizes topological sort or DFS-based algorithm as its implementation
- Fast: by the path relaxation property, you only have to do 1 iteration due to topological sort going from v<sub>r</sub> to v<sub>0</sub> (advantage) 

```
Time Complexity: θ(V + E)
- Depth-First Search: O(V + E)
- Relaxation: O(E)
```

## Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/dag2.png" alt="DAG Example" height="500" width="500" 
/>

Go in alphabetical order <br>

|   | u.d | u.f |
|---|-----|-----|
| a | 1 | 10 |
| b | 2 | 9 |
| c | 3 | 6 |
| d | 4 | 5 |
| e | 7 | 8 |

Topological Sort Order: < a, b, e, c, d > <br>
Relax the edges in topological order.

### Iteration 1

| Vertex | Initial | After Pass 1 | After Pass 2 | After Pass 3 | After Pass 4 |
|--------|---------|--------------|--------------|--------------|--------------|
| a | d=0<br/>(*)π=NIL |  |  |  |  |
| b | d=∞<br/>π=NIL | d=2<br/>π=a |  |  |  |
| c | d=∞<br/>π=NIL | d=6<br/>π=b | d=5<br/>(*)π=e |  |  |
| d | d=∞<br/>π=NIL | d=4<br/>π=a | d=3<br/>(*)π=c |  |  |
| e | d=∞<br/>π=NIL | d=6<br/>(*)π=a |  |  |  |


**Check `a`**

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/dag1.png" alt="Directed Acyclic Graph Example 1" height="100" width="100" 
/>

b.d relaxes from &infin; to **0 + 2 = 2**.

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/dag3.png" alt="Directed Acyclic Graph Example 2" height="100" width="100" 
/>

e.d relaxes from &infin; to **0 + 6 = 6**.

**Check `b`**

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/dag5.png" alt="Directed Acyclic Graph Example 5" height="100" width="100" 
/>

c.d relaxes from &infin; to **2 + 4 = 6**.

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/dag6.png" alt="Directed Acyclic Graph Example 6" height="100" width="100" 
/>

d.d relaxes from &infin; to **2 + 2 = 4**.

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/dag4.png" alt="Directed Acyclic Graph Example 4" height="100" width="100" 
/>

e.d is less than `b.d + w(b, e)`. No relaxing.

**Check `e`**

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/dag8.png" alt="Directed Acyclic Graph Example 8" height="100" width="100" 
/>

c.d relaxes from 6 to **6 - 1 = 5**.

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/dag9.png" alt="Directed Acyclic Graph Example 9" height="100" width="100" 
/>

d.d is less than `e.d + w(e, d)`. No relaxing.

**Check `c`**

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/dag10.png" alt="Directed Acyclic Graph Example 10" height="100" width="100" 
/>

d.d relaxes from 4 to ** 5 - 2 = 3**.

**Check `d`**

No outgoing edges. Skip.

### CONVERGED
d.d = 3 = &delta;(a, d) <br>
path is p: < a, e, c, d >

## Notes: PERT Charts

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/pertchart.png" alt="Pert Chart Example" height="400" width="400" 
/>

- Utilized in the software development cycle in software engineering
- Different module can run in parallel
- Identify the longest-path because we do not want any delays
  - The longest path is generally the bottleneck for potential delays
  - We do not want any delayes in this longest path
- One application of DAG algorithm
- However, this problem tries to look for the longest path (longest-path problem)
- 2 Options
  - Start with all non-start vertex having -&infin; and look for increasing `v.d`
  - Start with normal initialization using &infin;, but flip the signs of all weights