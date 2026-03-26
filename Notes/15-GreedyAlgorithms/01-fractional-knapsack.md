# Fractional Knapsack

## Knapsack Problem
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/fractionalknapsackproblem.png" alt="Relation Example" width="800" />
</p>

- Number of items: n
- Items: x1, x2, x3, ..., xn
- Weights: w1, w2, ..., wn
- Values: v1, v2, ..., vn

Representations:

- Item set: x = {xi | 1 <= i <= n}
- Weight set: w = {wi | 1 <= i <= n}
- Value set: v = {vi | 1 <= i <= n}

Additional notation:

- n = number of items in the full set
- M = number of items in the selected subset (optimal subset)

Specifications:

Objective function:

- Maximize FN = sum from i = 1 to n of (vi * xi)
- Equivalent form: sum of vi for all i in M
- Simple form: maximize total value

Constraint:

- Sum from i = 1 to n of (xi * wi) <= W
- Equivalent form: sum of wi for all i in M <= W

Decision variable:

- xi = 1 if the i-th item is selected
- xi = 0 otherwise