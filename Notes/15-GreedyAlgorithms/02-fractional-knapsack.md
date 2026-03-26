# Fractional Knapsack

## Fractional Knapsack Problem
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/fractionalknapsackproblem.png" alt="Fractional Knapsack Problem" width="800" />
</p>

- Fractional knapasack satisfies the greedy choice property
    - Optimal solution is done with greedy algorithm
- 0-1 knapsack does not satisfy the greedy choice property
    - Must use dynamic programming to obtain optimal substructure
- The algorithm is dominated by the sort step, rather than the greedy select step

```
Average Case: O(nlog(n))
Best Case (pre-sorted): O(n)
```

## Example: Slides
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/fractionknapsackexample.png" alt="Fractional Knapsack Problem" width="800" />
</p>

## Notes: Example

Capacity: **W = 14**

|  Item           | 1  | 2  | 3  |
|-----------------|----|----|----|
| Value           | 72 | 90 | 15 |
| Weight          | 6  | 9  | 5  |
| Value/Weight    | 12 | 10 | 3  |


**Goal: Maximize total value such that: Σ wᵢ xᵢ ≤ W**