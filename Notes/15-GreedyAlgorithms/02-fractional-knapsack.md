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
    - Sorting: O(nlog(n))
    - Selection: O(n)
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

### ❌ a) Pick lightest item first

- Pick item 3 (w = 5): remaining = 14 − 5 = 9  (v = 15)
- Pick item 1 (w = 6): remaining = 9 − 6 = 3  (v = 72)
- Take fraction of item 2: remaining = 3 - 3 = 0 (v = (90 / 9) × 3 = 30 )
- **Total value:** 15 + 72 + 30 = 117

### ❌ b) Pick highest value item first

- Pick item 2 (w = 9): remaining = 14 − 9 = 5  (v = 90)
- Take fraction of item 1 (w = 6): remaining = 5 − 5 = 0  (v = (72 / 6) x 5 = 60)
- **Total value:** 90 + 60 = 150

### ✅ c) Pick highest value/weight ratio (optimal)
- Pick item 1 (w = 6): remaining = 14 - 6 = 8 (v = 72)
- Take fraction of item 2 (w = 9): remaining = 8 - 8 = 0 (v = (90 / 9) x 8 = 80)
- **Total value:** 72 + 80 = 152


## Fractional Knapsack Satisfies the Greedy Properties

1. **Candidate Set:** The input of all possible items
2. **Selection Function:** pick item with max (vᵢ / wᵢ) ratio
3. **Feasibility Function:** Σ wᵢ xᵢ ≤ W
4. **Objective Function:** maximize Σ vᵢ xᵢ
5. **Solution Function:** all items have been entered in the sack OR capacity is reached