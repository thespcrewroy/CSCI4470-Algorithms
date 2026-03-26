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