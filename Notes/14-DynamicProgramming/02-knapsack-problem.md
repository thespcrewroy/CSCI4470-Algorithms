# Knapsack

## Notes: 01 Knapsack Problem

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/knapsackproblem.png" alt="Recursive Knapsack Example" width="800" />
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

**Specifications:**

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

## Slides: Bruteforce Appraoch
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/knapsackbruteforce.png" alt="Knapsack BurteforceExample" width="800" />
</p>

### Case 1: Capacity W = 10

Try combinations:

- Item 1 + Item 2 → weight = 4 + 5 = 9 ≤ 10
- Value = 5 + 8 = 13

Best solution:

- Items {1, 2} → Value = 13

### Case 2: Capacity W = 15

Try combinations:

- Item 2 + Item 4 → weight = 5 + 9 = 14 ≤ 15
- Value = 8 + 9 = 17

Best solution:

- Items {2, 4} → Value = 17

### Case 3: Capacity W = 17

Try combinations:

- Item 1 + Item 2 + Item 3 → weight = 4 + 5 + 7 = 16 ≤ 17
- Value = 5 + 8 + 7 = 20

Best Solution

- Items {1, 2, 3} → Value = 20

### Key Observations

Some solutions for smaller capacities can be part of larger solutions:

- Solution for W = 10 ({1,2}) is part of solution for W = 17 ({1,2,3}).

But not always:

- Solution for W = 15 ({2,4}) is not part of solution for W = 17.

### Why Dynamic Programming Is Needed

You must:

- Check all possible subproblems.
- Compare and pick the optimal combination.

You cannot assume:

- The best solution for a smaller capacity will always help build the best solution for a larger capacity.

## Notes: Dynamic Programming Recursive Solution

**Let Val(W,i) be the max value achievable using items {x<sub>i</sub> | 1 ≤ i ≤ n} and knapsack capacity W.**

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/recursiveknapsack.png" alt="Recursive Knapsack Example" width="800" />
</p>

* Case 1: If an item is too heavy (w<sub>i</sub> > W)
    * Ignore it (Val(W, i) = Val(W, i - 1))
* Case 2: If an item fits (w<sub>i</sub> &le; W), determine if it is optimal to add it or ignore it at each weight value (`max`)
    * Ignore the current item, and take the best value from the previous subproblem solution within that weight capacity (Val(W, i) = Val(W, i - 1))
    * Include the previous item(s) and add its value to the value of current item within that weight capacity (Val(w - w<sub>i</sub>, i - 1) + v<sub>i</sub>)

## Tutorial: Bottom Up Approach
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/knapsacktutorial1.png" alt="Bottom Up Example" width="800" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/knapsacktutorial2.png" alt="Knapsack Table Example" width="800" />
</p>

- First item: figure out all the best possible values for each capacity.
- Second item: reuse information about the optimal solution for the first-item to determine the optimal solution for the next item.
- Future items: repeat and expanding the same process as the second item.

### Table Without Redundant '0' Item Consideration

| Items / Capacity | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|------------------|---|---|---|---|---|---|---|---|
| v1=2, w1=3 (1)   |   |   |   |   |   |   |   |   |
| v2=2, w2=1 (2)   |   |   |   |   |   |   |   |   |
| v3=4, w3=3 (3)   |   |   |   |   |   |   |   |   |
| v4=5, w4=4 (4)   |   |   |   |   |   |   |   |   |
| v5=3, w5=2 (5)   |   |   |   |   |   |   |   |   |

- Shorter Arrow (select 0)
- Longer Arrow (select 1)

### Item 1
|  Wt | Val | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|-----|-----|---|---|---|---|---|---|---|---|
|  3  |  2  | 0 | 0 | 0 | 2 | 2 | 2 | 2 | 2 |
|  1  |  2  |   |   |   |   |   |   |   |   |
|  3  |  4  |   |   |   |   |   |   |   |   |
|  4  |  5  |   |   |   |   |   |   |   |   |
|  2  |  3  |   |   |   |   |   |   |   |   |

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

### Final Cost Table

|  Wt | Val | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|-----|-----|---|---|---|---|---|---|---|---|
|  3  |  2  | 0 | 0 | 0 | 2 | 2 | 2 | 2 | 2 |
|  1  |  2  | 0 | 2 | 2 | 2 | 4 | 4 | 4 | 4 |
|  3  |  4  | 0 | 2 | 2 | 4 | 6 | 6 | 6 | 8 |
|  4  |  5  | 0 | 2 | 2 | 4 | 6 | 7 | 7 | 9 |
|  2  |  3  | 0 | 2 | 3 | 5 | 6 | 7 | 9 | 10 |

### Selection Table

|  Wt | Val | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|-----|-----|---|---|---|---|---|---|---|---|
|  3  |  2  | 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 |
|  1  |  2  | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
|  3  |  4  | 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 |
|  4  |  5  | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 1 |
|  2  |  3  | 0 | 0 | 1 | 1 | 0 | 1 | 1 | 1 |


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

## Slides: Bottom Up
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/bottomup.png" alt="Bottom Up Example" width="800" />
</p>

**Time Complexity: O(nW)** <br>
**Space Complexity: O(nW)** <br> <br>

**Find solutions to small subproblems and progressively build up solutions to larger subproblems because maller subproblems have fewer items to choose from or smaller knapsack weight capacity.**


### 1. Cost Table

**Val(W, i) = max value for Knapsack(W, {x1, ..., xi}).**

| Wt | Val | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 |
|----|-----|---|---|---|---|---|---|---|---|---|---|----|----|----|----|----|----|
| 7  | 6   | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 6 | 6 | 6 | 6  | 6  | 6  | 6  | 6  | 6  |
| 4  | 5   | 0 | 0 | 0 | 0 | 5 | 5 | 5 | 6 | 6 | 6 | 6  | 11 | 11 | 11 | 11 | 11 |
| 5  | 8   | 0 | 0 | 0 | 0 | 5 | 8 | 8 | 8 | 8 | 13| 13 | 13 | 14 | 14 | 14 | 14 |
| 9  | 9   | 0 | 0 | 0 | 0 | 5 | 8 | 8 | 8 | 8 | 13| 13 | 13 | 14 | 14 | 17 | 17 |

**Optimal value = 17.**

### 2. Selection Table

**Sel(W, i) = 1 if x_i is put in the knapsack, and 0 otherwise**

| Wt | Val | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 |
|----|-----|---|---|---|---|---|---|---|---|---|---|----|----|----|----|----|----|
| 7  | 6   | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 1 | 1  | 1  | 1  | 1  | 1  | 1  |
| 4  | 5   | 0 | 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0  | 1  | 1  | 1  | 1  | 1  |
| 5  | 8   | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1  | 1  | 1  | 1  | 1  | 1  |
| 9  | 9   | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0  | 0  | 0  | 0  | 1  | 1  |

- Sel(4,15) = 1 → item 4 included (w4 = 9, v4 = 9)  
    - move to Sel(3, 15 - 9) = Sel(3,6)
- Sel(3,6) = 1 → item 3 included (w3 = 5, v3 = 8)  
    - move to Sel(2, 6 - 5) = Sel(2,1)
- Sel(2,1) = 0 → item 2 not included  
- Sel(1,1) = 0 → item 1 not included  

**Optimal selection = {x3, x4}**

## Quiz: Derive Value From Selection Table

The table below is a selection table for the knapsack problem. What is the optimal solution for this problem i.e optimal value (what is the maximum value) and weights (which weights are the part of the solution).

### Selection Table

| Wt | Val | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|----|-----|---|---|---|---|---|---|---|---|---|---|
| 3  | 14  | 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| 3  | 8   | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 1 | 1 |
| 2  | 6   | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | 1 |
| 2  | 7   | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | 1 |

1. Sel(4,9) = 1 → item x4 is included  
   - weight = 2
   - value = 7
   - move to Sel(3, 9 - 2) = Sel(3,7)

2. Sel(3,7) = 0 → item x3 is not included  
   - move to Sel(2,7)

3. Sel(2,7) = 1 → item x2 is included  
   - weight = 3
   - value = 8
   - move to Sel(1, 7 - 3) = Sel(1,4)

4. Sel(1,4) = 1 → item x1 is included  
   - weight = 3
   - value = 14
   - move to Sel(0, 4 - 3) = Sel(0,1)

**Optimal solution = {x1, x2, x4}** <br>
**Optimal weight = 3 + 3 + 2 = 8** <br>
**Optimal value = 14 + 8 + 7 = 29**

## Slides: Top Down

### Knapsack(15,4) recursive calls
- Knapsack(15,3)
- Knapsack(6,3)

| Wt | Val | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 |
|----|-----|---|---|---|---|---|---|---|---|---|---|----|----|----|----|----|----|
| 7  | 6   | o |   |   |   |   |   |   |   |   |   |    |    |    |    |    |    |
| 4  | 5   | o |   |   |   |   |   |   |   |   |   |    |    |    |    |    |    |
| 5  | 8   | o |   |   |   |   |   | X |   |   |   |    |    |    |    |    | X  |
| 9  | 9   | o |   |   |   |   |   |   |   |   |   |    |    |    |    |    | X  |

### Knapsack(15,3) recursive calls
- Knapsack(15,2)
- Knapsack(10,2)

| Wt | Val | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 |
|----|-----|---|---|---|---|---|---|---|---|---|---|----|----|----|----|----|----|
| 7  | 6   | o |   |   |   |   |   |   |   |   |   |    |    |    |    |    |    |
| 4  | 5   | o |   |   |   |   |   |   |   |   |   | X  |    |    |    |    | X  |
| 5  | 8   | o |   |   |   |   |   | X |   |   |   |    |    |    |    |    | X  |
| 9  | 9   | o |   |   |   |   |   |   |   |   |   |    |    |    |    |    | X  |

### Knapsack(6,3) recursive calls
- Knapsack(6,2)
- Knapsack(1,2)

| Wt | Val | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 |
|----|-----|---|---|---|---|---|---|---|---|---|---|----|----|----|----|----|----|
| 7  | 6   | o |   |   |   |   |   |   |   |   |   |    |    |    |    |    |    |
| 4  | 5   | o | X |   |   |   |   | X |   |   |   | X  |    |    |    |    | X  |
| 5  | 8   | o |   |   |   |   |   | X |   |   |   |    |    |    |    |    | X  |
| 9  | 9   | o |   |   |   |   |   |   |   |   |   |    |    |    |    |    | X  |

### Knapsack(15,2) recursive calls
- Knapsack(15,1)
- Knapsack(11,1)

| Wt | Val | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 |
|----|-----|---|---|---|---|---|---|---|---|---|---|----|----|----|----|----|----|
| 7  | 6   | o |   |   |   |   |   |   |   |   |   |    | X  |    |    |    | X  |
| 4  | 5   | o | X |   |   |   |   | X |   |   |   | X  |    |    |    |    | X  |
| 5  | 8   | o |   |   |   |   |   | X |   |   |   |    |    |    |    |    | X  |
| 9  | 9   | o |   |   |   |   |   |   |   |   |   |    |    |    |    |    | X  |

### Knapsack(10,2) recursive calls
- Knapsack(10,1)
- Knapsack(6,1)

| Wt | Val | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 |
|----|-----|---|---|---|---|---|---|---|---|---|---|----|----|----|----|----|----|
| 7  | 6   | o |   |   |   |   |   | X |   |   |   | X  | X  |    |    |    | X  |
| 4  | 5   | o | X |   |   |   |   | X |   |   |   | X  |    |    |    |    | X  |
| 5  | 8   | o |   |   |   |   |   | X |   |   |   |    |    |    |    |    | X  |
| 9  | 9   | o |   |   |   |   |   |   |   |   |   |    |    |    |    |    | X  |

### 6) Knapsack(6,2) recursive calls
- Knapsack(6,1) (memoized)
- Knapsack(2,1)

| Wt | Val | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 |
|----|-----|---|---|---|---|---|---|---|---|---|---|----|----|----|----|----|----|
| 7  | 6   | o |   | X |   |   |   | X |   |   |   | X  | X  |    |    |    | X  |
| 4  | 5   | o | X |   |   |   |   | X |   |   |   | X  |    |    |    |    | X  |
| 5  | 8   | o |   |   |   |   |   | X |   |   |   |    |    |    |    |    | X  |
| 9  | 9   | o |   |   |   |   |   |   |   |   |   |    |    |    |    |    | X  |

### 7) Knapsack(1,2) recursive calls
- Knapsack(1,1)
- Knapsack(0,1) (memoized)


| Wt | Val | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 |
|----|-----|---|---|---|---|---|---|---|---|---|---|----|----|----|----|----|----|
| 7  | 6   | X | X | X |   |   |   | X |   |   |   | X  | X  |    |    |    | X  |
| 4  | 5   | o | X |   |   |   |   | X |   |   |   | X  |    |    |    |    | X  |
| 5  | 8   | o |   |   |   |   |   | X |   |   |   |    |    |    |    |    | X  |
| 9  | 9   | o |   |   |   |   |   |   |   |   |   |    |    |    |    |    | X  |


### Final Recursion Tree
```
Knapsack(15,4)
|-- Knapsack(6,3)
|   |-- Knapsack(1,2)
|   |   |-- Knapsack(0,1) [memoized]
|   |   `-- Knapsack(1,1)
|   `-- Knapsack(6,2)
|       |-- Knapsack(2,1)
|       `-- Knapsack(6,1) [memoized]
`-- Knapsack(15,3)
    |-- Knapsack(10,2)
    |   |-- Knapsack(6,1)
    |   `-- Knapsack(10,1)
    `-- Knapsack(15,2)
        |-- Knapsack(11,1)
        `-- Knapsack(15,1)
```