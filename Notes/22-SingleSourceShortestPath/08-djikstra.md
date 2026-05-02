# Djikstra's Algorithm

- No negative weight edges allowed (disadvantage)
- Cheaper than Bellman-Ford (advantage)
- Useful for most real-world situations (advantage)
- More efficient for sparse graphs `< O(V^2)`
- Greedy Algorithm
- Implemented using a min-priority queue
- Processes vertices in the order of the shortest-cost from the source

```
Time Complexity: Vlog(V) + Elog(V) = (V + E)log(V) = O(Elog(V)) 
- Extract_Min: All the veertices are extracted once: O(Vlog(V))
- Decrease_Key: All the edges are relaxed once: O(Elog(V))
```

## Notes: Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/djikstra.png" alt="DAG Example" height="500" width="500" 
/>

| Vertex | Initial | After Pass 1 | After Pass 2 | After Pass 3 | After Pass 4 |
|--------|---------|--------------|--------------|--------------|--------------|
| s | d=0<br/>(*)π=NIL |  |  |  |  |
| t | d=∞<br/>π=NIL | d=10<br/>π=s | d=8<br/>(*)π=y  |  |  |
| x | d=∞<br/>π=NIL | d=14<br/>π=y | d=13<br/>π=z | d=8<br/>(*)π=t |  |
| y | d=∞<br/>π=NIL | d=5<br/>(*)π=s |  |  |  |
| z | d=∞<br/>π=NIL | d=7<br/>π=y |  |  |  |


**Check `s`**

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/djikstra1.png" alt="Djikstra Example" height="100" width="100" 
/>

t.d relaxes from &infin; to **0 + 10 = 10**.

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/djikstra2.png" alt="Djikstra Example" height="100" width="100" 
/>

y.d relaxes from &infin; to **0 + 5 = 5**.

**Check `y`**

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/heap1.png" alt="Djikstra Example" height="100" width="100" 
/>

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/djikstra3.png" alt="Djikstra Example" height="100" width="100" 
/>

t.d relaxes from 10 to **5 + 3 = 8**.

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/djikstra4.png" alt="Djikstra Example" height="100" width="100" 
/>

x.d relaxes from &infin; to **5 + 9 = 14**.

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/djikstra5.png" alt="Djikstra Example" height="100" width="100" 
/>

z.d relaxes from &infin; to **5 + 2 = 7**.

**Check `z`**

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/heap2.png" alt="Djikstra Example" height="100" width="100" 
/>

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/djikstra6.png" alt="Djikstra Example" height="100" width="100" 
/>

x.d relaxes from 14 to **7 + 6 = 13**.

**Check `t`**

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/djikstra8.png" alt="Djikstra Example" height="100" width="100" 
/>

x.d relaxes from 13 to **8 + 1 = 9**

y.d is less than `t.d + w(t, y)`. No relaxing.

**Check `x`**

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/djikstra7.png" alt="Djikstra Example" height="100" width="100" 
/>

z.d is less than `x.d + w(x, z)`. No relaxing.

**CONVERGED** <br>
s.x = 8 = &delta;(s, x) <br>
path is p: < s, y, t, x >

## Proof of Dijkstra's

### Theorem 22.6
Dijkstra's algorithm runs on a weighted directed graph `G(V, E)` with non-negative weight `w` and source vertex `s`, terminated with u.d = &delta;(s, u) for all vertices u &isin; V