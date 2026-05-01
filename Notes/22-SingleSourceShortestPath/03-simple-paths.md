# Simple Paths

- **Simple Path**: a graph that has no cycles
- Shortest paths are all simple paths.

## Negative Weight Cycles

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/neg.png" alt="negative Weight Cycle" width="600" />

path from vertex `a` to vertex `d`:
- p<sub>1</sub>: < a, b, c, d >
- w(p<sub>1</sub>) = 1 + 2 + 1 = 4

cycle `c`:
- c: < b, e, f, c, b >
- w(c) = - 1 - 2 - 1 + 2 = -2 < 0 (positive weight cycle)

path from vertex `a` to vertex `d` with a cycle:
- p<sub>2</sub>: < a, b, e, f, c, b, e, f, c, d >
- w(p<sub>2</sub>) = 1 - 1 - 2 - 1 + 2 - 1 - 2 - 1 + 1 = -4

- If you add a *negative weight cycle*, the shortest path value decreases.
- Adding the same cycle over and over again to the shortest path calculation keeps decreasing the weight by -2 each time.
- Thus, adding negative weight cycles means that the shortest distance calculation will never converge
- Having negative weights in a graph produces a high likliehood of developing negative cycles
- This is why Djikstra's Algorithm does not allow negative wights


## Positive Weight Cycles

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/pos.png" alt="Positive Weight Cycle" height="600" width="600" />

path from vertex `a` to vertex `d`:
- p<sub>1</sub>: < a, b, c, d >
- w(p<sub>1</sub>) = 1 + 2 + 1 = 4

cycle `c`:
- c: < b, e, f, c, b >
- w(c) = 1 - 1 + 2 + 2 = 4 > 0 (positive weight cycle)

path from vertex `a` to vertex `d` with a cycle:
- p<sub>2</sub>: < a, b, e, f, c, b, e, f, c, d >
- w(p<sub>2</sub>) = 1 + 1 - 1 + 2 + 2 + 1 - 1 + 2 + 1 = 8

- This section analyzes the effect of *positive weight cycles* on shortest path.
- The shortest path should be simple, neighter a negative nor positive weight cycle