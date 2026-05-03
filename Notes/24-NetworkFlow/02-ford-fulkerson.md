# Ford-Fulkerson Algorithm

1. Initialize flow `f` to 0
2. While for each augmenting path `p` in the residual network `G_f = {V, E}`
3. Augement flow `f` along path `p`
4. return `f`

- Does not put any emphasis on which augmenting path to select
- Must try all augmenting paths
- Does not put restrictions on what path to pick
- Convergence is actually &infin; because you can keep on picking paths

## Notes: Residual Network

*Tells you the remaining capacity left to increase the flow.*

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/back.png" alt="Ford Fulkerson Resid" width="400" 
/>

<br>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/back2.png" alt="Ford Fulkerson Resid" width="400" 
/>


- Example: E(s, w)
  - Flow: f(s, w) = 1
  - Capacity: c(s, w) = 3
  - Thus, we can forward the 2 residual units from `s` to `w`
  - Send the 1 flow unit back from `w` to `s`
- Example: E(w, x)
  - Flow: f(w, x) = 2
  - Capacity: c(w, x) = 2
  - No residual transition from `w` to `x`
  - Send the 2 flow unit back from `x` to `w`

## Notes: Augemnting Path

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/augment.png" alt="Ford Fulkerson Augemnt" width="400" 
/>

- Any path from source `s` to sync `t`
- The flow along this path is increased by the minimum weight capacity in that path
- For the above example, we would have to increase the flow by 1 unit along the path
- For the ones where we have to change the direction of the edge, we cancel it out and the edge becomes 0


<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/augmentation.png" alt="Ford Fulkerson Proof" width="400" 
/>

If `f` is the flow in network `G` and `f'` is the flow in residual network `Gf`, then the augmentation of flow `f` by `f'` is defined as the above formula.

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/conservation.png" alt="Ford Fulkerson Proof" width="400" 
/>

This satisfies the capacity and flow conservation properties.

### Capacity Constraint Satisfiability Proof

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/satisfiability.png" alt="Capacity Constraint Proof" width="400" 
/>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/satisfy2.png" alt="Capacity Constraint Proof" width="400" 
/>

- Establishes the flow the algorithm is calculating is a valid flow
- Augmentation flow (F&uarr;F') also satisfies the flow conservation property
  
## Notes: Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/ford.png" alt="Ford Fulkerson" width="400" 
/>

<br>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/residualnetwork.png" alt="Resiudal Network" width="400" 
/>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/augmentingpath.png" alt="Augmenting Path" width="400" 
/>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/returnf.png" alt="Return f" height="100" width="100" 
/>

*Iterate the 4 steps until there are no more augmenting paths.* <br>

> [!NOTE]\
> **Stopping Condition:** Eventually the graph will converge, and `s` and `t` will get disconnected from each other. <br>

## Notes: Example 2

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/ford1.png" alt="Ford Fulkerson Example 2" width="400" 
/>

### Iteration 1

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/resid2.png" alt="Ford Fulkerson Example 2" width="400" 
/>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/aug1.png" alt="Ford Fulkerson Example 2" width="400" 
/>

**|f| = 1**

### Iteration 2

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/resid3.png" alt="Ford Fulkerson Example 2" width="400" 
/>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/aug2.png" alt="Ford Fulkerson Example 2" width="400" 
/>

**|f| = 2**

### Iteration 3

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/resid4.png" alt="Ford Fulkerson Example 2" width="400" 
/>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/aug3.png" alt="Ford Fulkerson Example 2" width="400" 
/>

**|f| = 3**

### Iteration 4

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/resid5.png" alt="Ford Fulkerson Example 2" width="400" 
/>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/aug4.png" alt="Ford Fulkerson Example 2" width="400" 
/>

**|f| = 4**

### Iteration 5

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/resid6.png" alt="Ford Fulkerson Example 2" width="400" 
/>

**CONVERGED &rarr; Terminate** <br>
**|f| = Max_Flow**

### Cut

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/networkcut.png" alt="Ford Fulkerson Example 2" width="200" 
/>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/cutnow.png" alt="Ford Fulkerson Example 2" width="400" 
/>


- There is a cut at the termination of the Ford-Fulkerson algorithm that splits the network into two sets
- Set `s` represents all the vertices reachable from the start vertex `s`
- Set `t` holds the remaining vertices not in set `s`

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/cutequation.png" alt="Ford Fulkerson Cut Formula" width="400" 
/>

A `cut(S,T)` of a network flow graph `G={V, E}` is partition of `V` in `S` and `T` such that, in source s&isin;S and sync t&isin;T, the flow accross the `cut(S, T)` is defined as the above formula.

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/cutcapacity.png" alt="Ford Fulkerson Cut Capacity" width="400" 
/>

The capacity of the `cut(S,T)` is represented in the above formula.

## Notes: Proof

### Theorem 24.6 (Max-Flow Min-Cut Theorem)

If `f` is flow in flow network graph `G={V, E}` with source `s` and sync `t`, then the following conditions are equivalent:
1. `f` is maximum flow in `G={V, E}`
2. The residual network `Gf` contains no augmenting path
3. `|f| = C(S, T)` for cut `(S, T)` of `G={V, E}`

### Condition 1 => Condition 2

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/proofford1.png" alt="Ford Fulkerson Proof" width="400" 
/>

Let's say that flow `f` is maximum, but there are augmenting paths in the residual network.

### Condition 2 => Condition 3

In the last residual network, there is no path from source `s` to sync `t`.

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/proofford2.png" alt="Ford Fulkerson Proof" width="400" 
/>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/proofford3.png" alt="Ford Fulkerson Proof" width="400" 
/>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/proofford5.png" alt="Ford Fulkerson Proof" width="400" 
/>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/newton.png" alt="Ford Fulkerson Proof" width="250" 
/>

### Corollary 24.5

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/maxflowcorollary.png" alt="Ford Fulkerson Proof" width="400" 
/>
