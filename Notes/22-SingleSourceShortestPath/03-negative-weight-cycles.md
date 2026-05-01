# Negative Weight Cycles

## Positive Weight Cycles

This section analyzes the effective of a *positive weight cycle* on shortest path.

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/pos.png" alt="Positive Weight Cycle" height="600" width="600" />

path from vertex `a` to vertex `d`:
- p<sub>1</sub>:< a, b, c, d >
- w(p<sub>1</sub>) = 1 + 2 + 1

cycle `c`:
- c: < b, e, f, c, b >
- w(c) = 1 - 1 + 2 + 2 = 4 > 0 (positive weight cycle)

path from vertex `a` to vertex `d` with a cycle:
- p<sub>2</sub>: < a, b, e, f, c, b, e, f, c, d >
- w(p<sub>2</sub>) = 1 + 1 - 1 + 2 + 2 + 1 - 1 + 2 + 1
- w(p<sub>2</sub>) = 8