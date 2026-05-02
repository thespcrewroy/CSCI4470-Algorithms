# Bellman Ford Algorithm

- Allows negative edge weights
- Reports an error if `G={V, E}` contains a negative weight cycle (advantage)
- Expensive in cost compared to the other two SSSP algorithms (disadvantage)
- **Relax all the `E` edges `(V - 1)` times** to converge to shortest distance (v.d = &infin; -> &delta;(s, v))

```
Time Complexity: O(V*E)
```

## Example 

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/nig2.png" alt="Bellman Ford Example" height="500" width="500" 
/>

- You can pick and choose to start from any vertex
  - However, it is best practice to pick the source vertex `a`
  - We will run in alphabetical order, starting from source `a`
- 11 Edges and 8 Vertices
  - Relax all edges 7 times (`V - 1` times)
  - We may not run it the full `(V - 1)` iterations

### Iteration 1

| Vertex | Initial | After Pass 1 | After Pass 2 | After Pass 3 | After Pass 4 |
|--------|---------|--------------|--------------|--------------|--------------|
| a | d=0<br/>π=NIL |  |  |  |  |
| b | d=∞<br/>π=NIL | d=2<br/>π=a | | | |
| c | d=∞<br/>π=NIL | d=12<br/>π=a | d=7<br/>π=b |  |  |
| d | d=∞<br/>π=NIL | d=-1<br/>π=c |  | | |
| e | d=∞<br/>π=NIL |  |  |  |  |
| f | d=∞<br/>π=NIL | d=4<br/>π=a | | | |
| g | d=∞<br/>π=NIL | d=-2<br/>π=f  | |  |  |
| h | d=∞<br/>π=NIL | d=24<br/>π=f | d=7<br/>π=g |  | |

**Check `a`**
<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/itera1.png" alt="Bellman Ford Example Node A 1" height="100" width="100" 
/>

b.d relaxes from &infin; to **0 + 2 = 2**

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/itera2.png" alt="Bellman Ford Example Node A 2" height="100" width="100" 
/>

c.d relaxes from &infin; to **0 + 12 = 12**

f.d relaxes from &infin; to **0 + 4 = 4**

**Check `b`**

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/iterb1.png" alt="Bellman Ford Example Node B 1" height="100" width="100" 
/>

c.d relaxes from **12** to **2 + 5 = 7**


**Check `c`**

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/iterc1.png" alt="Bellman Ford Example Node C 1" height="100" width="100" 
/>

d.d relaxes from &infin; to **7 - 8 = -1**

**Check `d`**

No outgoing edges. Skip.

**Check `e`**

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/itere1.png" alt="Bellman Ford Example Node E 1" height="100" width="100" 
/>

a.d is less than `e.d + w(e, a)`. No relaxing.

c.d is less than `e.d + w(e, c)`. No relaxing.

**Check `f`**

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/iterf1.png" alt="Bellman Ford Example Node F 1" height="100" width="100" 
/>

g.d relaxes from &infin; to **4 - 6 = -2**

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/iterf2.png" alt="Bellman Ford Example Node F 2" height="100" width="100" 
/>

h.d relaxes from &infin; to **4 + 20 = 24**

**Check `g`**

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/iterg1.png" alt="Bellman Ford Example Node G 1" height="100" width="100" 
/>

h.d relaxes from 24 to **-2 + 9 = 7**

**Check `h`**

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/iterh1.png" alt="Bellman Ford Example Node H 1" height="100" width="100" 
/>

a.d is less than `h.d + w(h, a)`. No relaxing.


### Iteration 2

| Vertex | Initial | After Pass 1 | After Pass 2 | After Pass 3 | After Pass 4 |
|--------|---------|--------------|--------------|--------------|--------------|
| a | d=0<br/>π=NIL |  |  |  |  |
| b | d=2<br/>π=a |  | | | |
| c | d=7<br/>π=b | |  |  |  |
| d | d=-1<br/>π=c |  |  | | |
| e | d=∞<br/>π=NIL |  |  |  |  |
| f | d=4<br/>π=a |  | | | |
| g | d=-2<br/>π=fL |   | |  |  |
| h | d=7<br/>π=g | |  |  | |

**Check `a`**

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/itera4.png" alt="Bellman Ford Example Node A 4" height="100" width="100" 
/>

c.d is equal to `a.d + w(a, b, c)` (converged)

### CONVERGED
- h.d = 7 = &delta;(a, h)
- shortest distance between `a` and `h` is 7
- path is p: < a, f, g, h >