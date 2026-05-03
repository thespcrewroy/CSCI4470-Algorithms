# Johnson's Algorithm For Sparse Graphs

- Better than the DP solutions
- Good for sparse graphs
- More practical than other DP solutions

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/transform.png" alt="Transformed Johnson" width="400" 
/>

- Reweighs the graph such that there are no negative edges
- Utilizes Bellman-Ford algorithm to reweigh the graph
- Runs Djikstra on all the vertices in the reweighed graph
- h:V&rarr;R is a function that maps a vertex `v` to some real number `r`

```
Time Complexity: VE + E + VElog(V) = O(VElog(V))
- Bellman-Ford to get h(v) value or detect negative cycles: O(VE)
- Using h(v) value, perform the transformation to get w-hat(u,v): O(E)
- Running Djikstra's on all vertices: V*O(Elog(V)) = O(VElog(V))
```

## Notes: Objective Function

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/objjohn.png" alt="Johnson Algo Objective Function" length="400" width="400" 
/>

### Updating Weights Example

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/p1.png" alt="Updating Weights" length="400" width="400" 
/>

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/p2.png" alt="Updating Weights" length="400" width="500" 
/>

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/p3.png" alt="Updating Weights" length="200" width="200" 
/>

## Notes: Proof
<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/proof1.png" alt="Johnson Proof" length="200" width="200" 
/>

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/proof2.png" alt="Johnson Proof" length="400" width="400" 
/>

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/proof3.png" alt="Johnson Proof" length="400" width="400" 
/>


## Notes: Example

**Given a constraint graph.**

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/constraint.png" alt="Johnson Example" length="300" width="300" 
/>

**Add s<sub>0</sub> by connecting it to all vertices with a 0 transition.**

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/constraint2.png" alt="Johnson Example" length="400" width="400" 
/>

**Run Bellman-Ford on s.**

&delta;(s, v<sub>1</sub>) = h(v<sub>1</sub>) = <br>
&delta;(s, v<sub>2</sub>) = h(v<sub>2</sub>) = <br>
&delta;(s, v<sub>3</sub>) = h(v<sub>3</sub>) = <br>
&delta;(s, v<sub>4</sub>) = h(v<sub>4</sub>) = <br>

## Slides: Example

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/johnson2.png" alt="Johnson Example 2" length="400" width="400" 
/>

**Run Bellman-Ford on s:**

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/johnson21.png" alt="Johnson Example 2" length="300" width="300" 
/>

*Do positive edge w&#x302;(1,2)*

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/posedge.png" alt="Johnson Example 2" length="300" width="300" 
/>

*Do negative edge w&#x302;(1,5)*

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/negedge.png" alt="Johnson Example 2" length="300" width="300" 
/>

*Do the remining edges...*

**Obtain the transformed graph.**

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/trans.png" alt="Johnson Example 2" length="300" width="300" 
/>
