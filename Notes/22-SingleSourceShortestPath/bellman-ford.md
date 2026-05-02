# Bellman-Ford Algorithm

## Overview
The Bellman-Ford algorithm finds the shortest path from a source vertex to all other vertices in a weighted directed graph, even with negative edge weights (as long as there are no negative cycles).

## Example Execution Table

The table below traces the execution of Bellman-Ford starting from source vertex `a`:

| Vertex | Initial | After Pass 1 | After Pass 2 | After Pass 3 | After Pass 4 |
|--------|---------|--------------|--------------|--------------|--------------|
| a | d=0<br/>π=NIL | d=0<br/>π=NIL | d=0<br/>π=NIL | d=0<br/>π=NIL | d=0<br/>π=NIL |
| b | d=∞<br/>π=NIL | d=2<br/>π=a | d=2<br/>π=a | d=2<br/>π=a | d=2<br/>π=a |
| c | d=∞<br/>π=NIL | d=12<br/>π=a | d=7<br/>π=b | d=7<br/>π=b | d=7<br/>π=b |
| d | d=∞<br/>π=NIL | d=∞<br/>π=NIL | d=-1<br/>π=c | d=-1<br/>π=c | d=-1<br/>π=c |
| e | d=∞<br/>π=NIL | d=∞<br/>π=NIL | d=∞<br/>π=NIL | d=∞<br/>π=NIL | d=∞<br/>π=NIL |
| f | d=∞<br/>π=NIL | d=4<br/>π=a | d=4<br/>π=a | d=4<br/>π=a | d=4<br/>π=a |
| g | d=∞<br/>π=NIL | d=∞<br/>π=NIL | d=-2<br/>π=f | d=-2<br/>π=f | d=-2<br/>π=f |
| h | d=∞<br/>π=NIL | d=∞<br/>π=NIL | d=24<br/>π=f | d=7<br/>π=g | d=7<br/>π=g |

## Algorithm Steps

1. **Initialization**: Set distance to source `d[a] = 0` and all others to `∞`.
2. **Relaxation**: For each of the (V-1) passes, relax every edge `(u, v)`:
   - If `d[u] + w(u, v) < d[v]`, then update `d[v] = d[u] + w(u, v)` and `π[v] = u`
3. **Negative Cycle Check**: After (V-1) passes, verify that no edge can be relaxed further. If any edge can be relaxed, a negative cycle exists.

## Key Properties

- **Time Complexity**: O(VE) — we iterate V-1 times, and each iteration checks all E edges
- **Space Complexity**: O(V) — for storing distances and predecessors
- **Handles Negative Weights**: Unlike Dijkstra's algorithm, Bellman-Ford works with negative edge weights
- **Detects Negative Cycles**: Can identify if a negative cycle reachable from the source exists

## Pseudocode

```
BELLMAN-FORD(G, w, s)
    INITIALIZE-SINGLE-SOURCE(G, s)
    for i = 1 to |V| - 1
        for each edge (u, v) in E
            RELAX(u, v, w)
    for each edge (u, v) in E
        if v.d > u.d + w(u, v)
            return FALSE  // negative cycle detected
    return TRUE
```

## RELAX Operation

```
RELAX(u, v, w)
    if u.d + w(u, v) < v.d
        v.d = u.d + w(u, v)
        v.π = u
```
