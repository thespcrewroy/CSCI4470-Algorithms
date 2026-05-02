# Djikstra's Algorithm

- No negative weight edges allowed (disadvantage)
- Cheaper than Bellman-Ford (advantage)
- Useful for most real-world situations (advantage)
- More efficient for sparse graphs `< O(V^2)`
- Greedy Algorithm
- Implemented using a min-priority queue

```
Time Complexity: O(V^2)
```

## Notes: Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/djikstra.png" alt="DAG Example" height="500" width="500" 
/>

### Iteration 1

| Vertex | Initial | After Pass 1 | After Pass 2 | After Pass 3 | After Pass 4 |
|--------|---------|--------------|--------------|--------------|--------------|
| s | d=0<br/>π=NIL |  |  |  |  |
| t | d=∞<br/>π=NIL | d=10<br/>π=s | d=8<br/>π=y  |  |  |
| x | d=∞<br/>π=NIL | d=14<br/>π=y |  |  |  |
| y | d=∞<br/>π=NIL | d=5<br/>π=s |  |  |  |
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