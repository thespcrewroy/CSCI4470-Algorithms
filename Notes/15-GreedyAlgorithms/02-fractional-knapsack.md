# Fractional Knapsack

## Knapsack Problem
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/fractionalknapsackproblem.png" alt="Fractional Knapsack Problem" width="800" />
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

