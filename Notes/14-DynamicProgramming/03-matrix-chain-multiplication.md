# Matrix Chain Multiplication

## Notes: Matrix Chain Multiplication Problem

- Different parenthesizations (orders of multiplication) affect the total multiplication cost
- Matrix multiplication is associative  
    - (A1 A2) A3 = A1 (A2 A3)  
    - Both give the same result, but the cost (number of multiplications) changes depending on the order

**Goal: Find the parenthesization that minimizes the total number of scalar multiplications**

## Slides: Matrix Chain Multiplication – Cost Calculation

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/costanalysis.png" alt="Fractional Knapsack Problem Example" width="800" />
</p>


### Matrix Multiplication Formula

For matrices:
- A is of size p × q  
- B is of size q × r  
- Result C is of size p × r  

Each entry:
C[i, j] = Σ (A[i, k] × B[k, j]) for k = 1 to q

### Cost Analysis

- Number of entries in C:
  → p × r

- Cost to compute each entry:
  → q multiplications (and q - 1 additions)

- Total cost:
  → p × q × r scalar multiplications


## Notes: Cost Analysis Example

### Given Matrices

| Matrix | Dimensions |
|--------|-----------|
| A1     | 10 × 100  |
| A2     | 100 × 5   |
| A3     | 5 × 50    |

---

### Case 1: ((A1 A2) A3)

Step 1: Multiply A1 × A2  
- Cost = 10 × 100 × 5 = 5,000  
- Result size = 10 × 5  

Step 2: Multiply (A1A2) × A3  
- Cost = 10 × 5 × 50 = 2,500  
- Result computations = 5,000 + 2,500 = **7,500**

---

### Case 2: (A1 (A2 A3))

Step 1: Multiply A2 × A3  
- Cost = 100 × 5 × 50 = 25,000  
- Result size = 100 × 50  

Step 2: Multiply A1 × (A2A3)  
- Cost = 10 × 100 × 50 = 50,000  
- Result computations = 25,000 + 50,000 = **75,000**

### Comparison

| Case | Parenthesization | Cost |
|------|------------------|------|
| 1    | ((A1 A2) A3)     | 7,500 |
| 2    | (A1 (A2 A3))     | 75,000 |

### Key Insight

- Both give the **same resultant multiplication order**
- But cost is **very different** since parenthesizaation is different.
- Case 1 is **10× faster**
- Thus, the order of multiplication significantly affects performance.
- Optimization goal: Choose the order that minimizes total scalar multiplications


## Notes: Dynamic Programming Recursive Solution

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/matrixchaintheory.png" alt="Fractional Knapsack Problem Example" width="800" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/recursivematrixchain.png" alt="Fractional Knapsack Problem Example" width="800" />
</p>

| Term | Meaning |
|------|--------|
| A_i ... A_j | The chain of matrices from i to j |
| k | The position where we split the chain |
| cost(A_i ... A_k) | Optimal cost of multiplying the left subchain |
| cost(A_{k+1} ... A_j) | Optimal cost of multiplying the right subchain |
| p_{i-1} p_k p_j | Cost of multiplying the two resulting matrices |
| min | Choose the split k that gives the smallest total cost |

### Paranthesizing (splitting the term
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/splitting.png" alt="Fractional Knapsack Problem Example" width="800" />
</p>

### Time Complexity

**T(n) = O(n^3)**
- Comes from 3 nested loops
- Each loop runs up to n
- Total operations ≈ n × n × n = n^3

## Notes: Bruteforce Approach

List all possible parenthesizations and compute the cost for each:

1. (A1 (A2 (A3 A4))) → m1  
2. (A1 ((A2 A3) A4)) → m2  
3. ((A1 A2) A3) A4 → m3  
4. (A1 A2)(A3 A4) → m4  
5. ((A1 (A2 A3)) A4) → m5  

**Optimal cost = min(m1, m2, m3, m4, m5)**