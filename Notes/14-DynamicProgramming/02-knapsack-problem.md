# Fractional Knapsack

## Knapsack Problem
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/fractionalknapsackproblem.png" alt="Relation Example" width="800" />
</p>

- Number of items: n
- Items: x<sub>1</sub>, x<sub>2</sub>, x<sub>3</sub>, ..., x<sub>n</sub>
- Weights: w<sub>1</sub>, w<sub>2</sub>, ..., w<sub>n</sub>
- Values: v<sub>1</sub>, v<sub>2</sub>, ..., v<sub>n</sub>

Representations:

- Item set: x = {x<sub>i</sub> | 1 <= i <= n}
- Weight set: w = {w<sub>i</sub> | 1 <= i <= n}
- Value set: v = {v<sub>i</sub> | 1 <= i <= n}

Additional notation:

- n = number of items in the full set
- M = number of items in the selected subset (optimal subset)

Specifications:

Objective function:

- Maximize F<sub>N</sub> = ∑<sub>i=1</sub><sup>n</sup> (v<sub>i</sub> * x<sub>i</sub>)
- Equivalent form: ∑<sub>i∈M</sub> v<sub>i</sub>
- Simple form: maximize total value

Constraint:

- ∑<sub>i=1</sub><sup>n</sup> (x<sub>i</sub> * w<sub>i</sub>) ≤ W
- Equivalent form: ∑<sub>i∈M</sub> w<sub>i</sub> ≤ W

Decision variable:

- x<sub>i</sub> = 1 if the i-th item is selected
- x<sub>i</sub> = 0 otherwise

## Tutorial: Bottom Up Approach
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/knapsacktutorial1.png" alt="Relation Example" width="800" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/knapsacktutorial2.png" alt="Relation Example" width="800" />
</p>

- First item: figure out all the best possible values for each capacity.
- Second item: reuse information about the optimal solution for the first-item to determine the optimal solution for the next item
- Complete other items by repeating and expanding the same process.

### For Each Cell

| Items / Capacity | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|------------------|---|---|---|---|---|---|---|---|
| Empty (0)        | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| v1=2, w1=3 (1)   |   |   |   |   |   |   |   |   |
| v2=2, w2=1 (2)   |   |   |   |   |   |   |   |   |
| v3=4, w3=3 (3)   |   |   |   |   |   |   |   |   |
| v4=5, w4=4 (4)   |   |   |   |   |   |   |   |   |
| v5=3, w5=2 (5)   |   |   |   |   |   |   |   |   |

- Shorter Arrow (select 0): not including the current item, but instead taking the best value from before within that capacity.
  - v<sub>i</sub> of W<sub>j</sub> = v<sub>(i - 1)</sub> of W<sub>j</sub>
- Longer Arrow (select 1): include the previous item and add its value to the value of current item.
  - v<sub>i</sub> of W<sub>j</sub> = [v<sub>(i - 1)</sub> of W<sub>(j - w_i)</sub>] + v<sub>i</sub>

- If w<sub>i</sub> < W<sub>i</sub>: use the shorter arrow.
- If w<sub>i</sub> ≥ W<sub>i</sub>: compare the shorter and longer arrow, and use the one that is larger.

### Item 1
| Items / Capacity | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|------------------|---|---|---|---|---|---|---|---|
| Empty (0)        | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| v1=2, w1=3 (1)   | 0 | 0 | 0 | 2 | 2 | 2 | 2 | 2 |
| v2=2, w2=1 (2)   |   |   |   |   |   |   |   |   |
| v3=4, w3=3 (3)   |   |   |   |   |   |   |   |   |
| v4=5, w4=4 (4)   |   |   |   |   |   |   |   |   |
| v5=3, w5=2 (5)   |   |   |   |   |   |   |   |   |

Item 1: [v<sub>1</sub> = 2, w<sub>1</sub> = 3]

- (1,0) → {w<sub>1</sub> = 3 > 0} → best solution: 0
  - Short Arrow: (0,0) = 0
- (1,1) → {w<sub>1</sub> = 3 > 1} → best solution: 0
  - Short Arrow: (0,1) = 0
- (1,2) → {w<sub>1</sub> = 3 > 2} → best solution: 0
  - Short Arrow: (0,2) = 0
- (1,3) → {w<sub>1</sub> = 3 = 3} → best solution: 2
  - Short Arrow: (0,3) = 0
  - Long Arrow: (0,0) = 0 + 2 = 2
- (1,3) → {w<sub>1</sub> = 3 < 4} → best solution: 2
  - Short Arrow: (0,4) = 0
  - Long Arrow: (0,1) = 0 + 2 = 2
- (1,3) → {w<sub>1</sub> = 3 < 5} → best solution: 2
  - Short Arrow: (0,5) = 0
  - Long Arrow: (0,2) = 0 + 2 = 2
- (1,3) → {w<sub>1</sub> = 3 < 6} → best solution: 2
  - Short Arrow: (0,6) = 0
  - Long Arrow: (0,3) = 0 + 2 = 2
- (1,3) → {w<sub>1</sub> = 3 < 7} → best solution: 2
  - Short Arrow: (0,7) = 0
  - Long Arrow: (0,4) = 0 + 2 = 2

### Item 2

| Items / Capacity | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|------------------|---|---|---|---|---|---|---|---|
| Empty (0)        | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| v1=2, w1=3 (1)   | 0 | 0 | 0 | 2 | 2 | 2 | 2 | 2 |
| v2=2, w2=1 (2)   | 0 | 2 | 2 | 2 | 4 | 4 | 4 | 4 |
| v3=4, w3=3 (3)   |   |   |   |   |   |   |   |   |
| v4=5, w4=4 (4)   |   |   |   |   |   |   |   |   |
| v5=3, w5=2 (5)   |   |   |   |   |   |   |   |   |

Item 2: [v<sub>2</sub> = 2, w<sub>2</sub> = 1]

- (2,0) → {w<sub>2</sub> = 1 > 0} → best solution: 0
  - Short Arrow: (1,0) = 0
- (2,1) → {w<sub>2</sub> = 1 = 1} → best solution: 2
  - Short Arrow: (1,1) = 0
  - Long Arrow: (1,0) = 0
- (2,2) → {w<sub>2</sub> = 1 < 2} → best solution: 2
  - Short Arrow: (1,2) = 0
  - Long Arrow: (1,1) = 0 + 2 = 2
- (2,3) → {w<sub>2</sub> = 1 < 3} → best solution: 2
  - Short Arrow: (1,3) = 2
  - Long Arrow: (1,2) = 0 + 2 = 2
- (2,4) → {w<sub>2</sub> = 1 < 4} → best solution: 4
  - Short Arrow: (1,4) = 2
  - Long Arrow: (1,3) = 2 + 2 = 4
- (2,5) → {w<sub>2</sub> = 1 < 5} → best solution: 4
  - Short Arrow: (1,5) = 2
  - Long Arrow: (1,4) = 2 + 2 = 4
- (2,6) → {w<sub>2</sub> = 1 < 6} → best solution: 4
  - Short Arrow: (1,6) = 2
  - Long Arrow: (1,5) = 2 + 2 = 4
- (2,7) → {w<sub>2</sub> = 1 < 7} → best solution: 4
  - Short Arrow: (1,7) = 2
  - Long Arrow: (1,6) = 2 + 2 = 4

### Item 3
| Items / Capacity | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|------------------|---|---|---|---|---|---|---|---|
| Empty (0)        | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| v1=2, w1=3 (1)   | 0 | 0 | 0 | 2 | 2 | 2 | 2 | 2 |
| v2=2, w2=1 (2)   | 0 | 2 | 2 | 2 | 4 | 4 | 4 | 4 |
| v3=4, w3=3 (3)   | 0 | 2 | 2 | 4 | 6 | 6 | 6 | 8 |
| v4=5, w4=4 (4)   |   |   |   |   |   |   |   |   |
| v5=3, w5=2 (5)   |   |   |   |   |   |   |   |   |

### Item 4
| Items / Capacity | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|------------------|---|---|---|---|---|---|---|---|
| Empty (0)        | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| v1=2, w1=3 (1)   | 0 | 0 | 0 | 2 | 2 | 2 | 2 | 2 |
| v2=2, w2=1 (2)   | 0 | 2 | 2 | 2 | 4 | 4 | 4 | 4 |
| v3=4, w3=3 (3)   | 0 | 2 | 2 | 4 | 6 | 6 | 6 | 8 |
| v4=5, w4=4 (4)   | 0 | 2 | 2 | 4 | 6 | 7 | 7 | 9 |
| v5=3, w5=2 (5)   |   |   |   |   |   |   |   |   |

### Item 5

| Items / Capacity | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|------------------|---|---|---|---|---|---|---|---|
| Empty (0)        | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| v1=2, w1=3 (1)   | 0 | 0 | 0 | 2 | 2 | 2 | 2 | 2 |
| v2=2, w2=1 (2)   | 0 | 2 | 2 | 2 | 4 | 4 | 4 | 4 |
| v3=4, w3=3 (3)   | 0 | 2 | 2 | 4 | 6 | 6 | 6 | 8 |
| v4=5, w4=4 (4)   | 0 | 2 | 2 | 4 | 6 | 7 | 7 | 9 |
| v5=3, w5=2 (5)   | 0 | 2 | 3 | 5 | 6 | 7 | 9 | 10 |

### Best Value

**Best value of selecting a subset of 5 items can be found at the bottom-right corner (v_optimal = 10)**

### Optimal Item Choices

- Start in the right corner and work backwards.
- We include an element if the current value and the value in the row above it differ.
- Justification: if the two values differ, then the row we are on must have had its item included, else the value would not have changed.

### Item Selection Process

- 7 kg remain: 10 != 9 → Include Item 5 [v<sub>1</sub> = 3, w<sub>1</sub> = 2]
    - Subtract weight → 7 - 2 = 5 → Head to Column 5
- 5 kg remain: 7 != 6 → Include Item 4 [v<sub>1</sub> = 5, w<sub>1</sub> = 4]
    - Subtract weight → 5 - 4 = 1 → Head to Column 1
- 1 kg remain: 2 = 2 → Ignore Item 3
- 1 kg remain: 2 != 0 → Include Item 2 [v<sub>2</sub> = 2, w<sub>2</sub> = 1]
    - Subtract weight → 1 - 1 = 0 → Head to Column 0
- 0 kg remain

**We selected items: {x<sub>2</sub>, x<sub>4</sub>, x<sub>5</sub>}** <br>
  - Item values add up to: v = 2 + 5 + 3 = 10
  - Item weights add up to: w = 1 + 4 + 2 = 7

