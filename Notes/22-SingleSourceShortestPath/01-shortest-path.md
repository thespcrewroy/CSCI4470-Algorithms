# Shortest Path Problem

- path p< v<sub>0</sub>, v<sub>1</sub>, ..., v<sub>k</sub> >
- path from vertex v<sub>0</sub> to v<sub>k</sub>

## w(p)

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/wp.png" alt="w(p)" height="300" width="300" />
</p>

**Example**

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/wp2.png" alt="w(p) Example" height="150" width="300" />
</p>

w(p) = -1 + 2 + -1 = 0

## &delta;(s, u)

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/su.png" alt=delta(s, u)" height="300" width="300" />

- &delta;(s, u): shortest path from vertex `s` to vertex `u`
- &delta;(s, u) = &infin;: if there is no path from `s` to `u`

## Optimal Subsructure Lemma

Shortest path calculation has the optimal substructure.

- p: < v<sub>0</sub>, v<sub>1</sub>, ..., v<sub>k</sub> >
- p<sub>0k</sub> is the shortest path from v<sub>0</sub> to v<sub>k</sub>
- p<sub>0k</sub> = p<sub>0i</sub> (shortest) + p<sub>ij</sub> (shortest) + p<sub>jk</sub> (shortest)
- Lemma: all paths used were optimal, so p<sub>0k</sub> is optimal

## Optimal Substructure Proof by Contradiction
- p<sub>0k</sub> = p<sub>0i</sub> (shortest) + p<sub>ij</sub> (shortest) + p<sub>jk</sub> (shortest)
- Proof by Contrafuction: all paths used were optimal, so p<sub>0k</sub>' is NOT optimal (not shortest)
- Assumption: w<sub>(P0k)</sub> <> w<sub>(P0k')</sub>

Given: w<sub>(Pij)</sub> > w<sub>(Pij')</sub> <br>
w<sub>(P0k)</sub> = w<sub>(P0i)</sub> + w<sub>(Pij)</sub> + w<sub>(Pjk)</sub> <br>
w<sub>(P0k')</sub> = w<sub>(P0i)</sub> + w<sub>(Pij')</sub> + w<sub>(Pjk)</sub> <br>
w<sub>(P0k)</sub> - w(P0k') = w<sub>(Pij)</sub> + w<sub>(Pij')</sub> <br>
w<sub>(P0k)</sub> - w<sub>(P0k')</sub> = w<sub>(Pij)</sub> + w<sub>(Pij')</sub> <br>
w<sub>(P0k)</sub> - w<sub>(P0k')</sub> > 0
w<sub>(P0k)</sub> > w<sub>(P0k')</sub>