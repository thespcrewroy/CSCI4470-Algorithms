# Cut

## Notes: Definition

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/cut.png" alt="Cut" height="500" />
</p>

> 8(a,h), 11(b,h), 8(b,c), 7(c,d), 14(d,f), 10(f,e) are edges crossing the cut

- A cut `(s, v - s)` of an unidrected graph `G(V, E)` is a partition of vertices `v`.
- Any edge you add accross the cut will not form a cycle
- Any edge added within a cut will form a cycle
- edge `E(u, v)` crosses the cut `(s, v - s)` if one of its endpoints is in `s` and the other end point is in `v - s`.

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/respect.png" alt="Cut Respect" width="500"  />
</p>

A cut respects a set `A` of edges if no edges in `A` crosses the cut.

## Notes: Light Edge

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/accrosscut.png" alt="Safe Edge Cut" width="500" />
</p>

- A light edge crossing the cut is the minimum weight edge out of all the edges crossing the cut.
- This edge becomes the safe edge
- MST Algorithms find the safe edge, add to spanning tree, and then iterate
- In the example from the *Definition* section, (c,d) is considered the light edge

### Theorem 15.1

Let `G={V,E}` be a connected undirected weighted graph with weight `W` defined on edge `E` <br>
Let `A` be a subset of `E` that is included in some minimum spanning tree for graph `G ` <br>
Let `(s, v - s)` be any cut of `G` that respects `A` and lets `(u, v)` be a light edge crossing the cut <br>
**The edge (u, v) must be a safe edge for A.**

## Homework: Minimum Weight Edge

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/hw4-7.png" alt="Ligh Edge Examplet"  />
</p>


### Theorem 15.1

Let `G={V,E}` be a connected undirected weighted graph with weight `W` defined on edge `E` <br>
Let `A` be a subset of `E` that is included in some minimum spanning tree for graph `G ` <br>
Let `(s, v - s)` be any cut of `G` that respects `A` and lets `(u, v)` be a light edge crossing the cut <br>
**The edge (u, v) must be a safe edge for A.**