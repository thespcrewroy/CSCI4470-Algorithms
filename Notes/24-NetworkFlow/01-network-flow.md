# Network Flow

- Has both a source vertex `s` and sync vertex `t`
- Has applications in supply chain, where `s` is the factory producing goods while `t` is the destination where the goods have to reach

## Notes: Capacity Graph

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/network1.png" alt="Network Capacity Graph" width="400" 
/>

- Each weight represents a weight capacity
- Example: Capacity of E(s, x) is 3
  - C(s, x) = 3
  - Through the edge (s, x), either 0, 1, 2, or 3 units can pass
- The internal node edges determine how the units get transfered through the network
- Goal: shift max amount of flow from source to sync, which depends on the flow of the internal nodes

## Notes: Flow Graph

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/network2.png" alt="Network Flow Graph" width="400" 
/>

- Example: E(s, w)
  - Flow from `s` to `w` is 1: f(s, w) = 1
  - Capacity of edge (s, w) is 3: c(s, w) = 3
- A flow in `G={V, E}` is a real value function f:vxv&rarr;R that satisfied two properties
  - Capacity constraint
  - Flow conservation


## Notes: Capacity Constraint Property

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/capconstraint.png" alt="Capacity Constraint" length="300" width=300" 
/>

## Notes: Flow Conservation Property

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/flowcons.png" alt="Flow Conservation" length="300" width=300" 
/>

- Flow conservation for all vertices u &isin; v - {s, t}
- For each vertex, the flow coming in and going out is equal in sizes
- Property yeilds true for all the vertices except source `s` and sync `t`

## Notes: Flow Magnitude `|f|`

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/maxflow.png" alt="Full Flow" length="500" width=500" 
/>


<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/network2.png" alt="Network Flow Graph" width="400" 
/>

> |f| = 3 for this graph because the flow values going out of source vertex `s` adds up to 3. This is the value to maximize.

## Network Flow Algorithms
1. Ford-Fulkerson (Greedy)
2. Edmonds-Karp (Greedy)
