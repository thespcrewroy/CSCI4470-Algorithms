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