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


### Case 1: ((A1 A2) A3)

Step 1: Multiply A1 × A2  
- Cost = 10 × 100 × 5 = 5,000  
- Result size = 10 × 5  

Step 2: Multiply (A1A2) × A3  
- Cost = 10 × 5 × 50 = 2,500  
- Result computations = 5,000 + 2,500 = **7,500**


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

### Paranthesizing (splitting the term)
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

## Notes: Bottom Up Approach

### Input

p = {3, 9, 8, 2, 5}

Matrices:
- A1 = 3 × 9
- A2 = 9 × 8
- A3 = 8 × 2
- A4 = 2 × 5

Goal:
→ Compute m[1,4]


## Base Case A<sub>i</sub>

- i = 1; k = 1; j = 1
    - m[1,1] = 0  
- i = 2; k = 2; j = 2
    - m[2,2] = 0  
- i = 3; k = 3; j = 3
    - m[3,3] = 0  
- i = 4; k = 4; j = 4
    - m[4,4] = 0  


## Compute A<sub>i</sub>A<sub>i+1</sub>

- i = 1; k = 1; j = 2
    - m[1,2] = (p<sub>0</sub>)(p<sub>1</sub>)(<sub>2</sub>) = (3)(9)(8) = 216
    - s[1,2] = 1

- i = 2; k = 2; j = 3
    - m[2,3] = (p<sub>1</sub>)(p<sub>2</sub>)(p<sub>3</sub>)(9)(8)(2) = 144  
    - s[2,3] = 2  

- i = 3; k = 3; j = 4
    - m[3,4] = (p<sub>2</sub>)(p<sub>3</sub>)(p<sub>4</sub>) = (8)(2)(5) = 80  
    - s[3,4] = 3  

---

## Step 3: Chains of Length 3 (Ai Ai+2)

### m[1,3]

Try all k:

- k = 1  
  = m[1,1] + m[2,3] + (3)(9)(2)  
  = 0 + 144 + 54 = 198  

- k = 2  
  = m[1,2] + m[3,3] + (3)(8)(2)  
  = 216 + 0 + 48 = 264  

→ m[1,3] = min(198, 264) = **198**  
→ s[1,3] = 1  

---

### m[2,4]

- k = 2  
  = m[2,2] + m[3,4] + (9)(8)(5)  
  = 0 + 80 + 360 = 440  

- k = 3  
  = m[2,3] + m[4,4] + (9)(2)(5)  
  = 144 + 0 + 90 = 234  

→ m[2,4] = min(440, 234) = **234**  
→ s[2,4] = 3  

---

## Step 4: Chains of Length 4 (Full Chain)

### m[1,4]

Try all k:

- k = 1  
  = m[1,1] + m[2,4] + (3)(9)(5)  
  = 0 + 234 + 135 = 369  

- k = 2  
  = m[1,2] + m[3,4] + (3)(8)(5)  
  = 216 + 80 + 120 = 416  

- k = 3  
  = m[1,3] + m[4,4] + (3)(2)(5)  
  = 198 + 0 + 30 = 228  

→ m[1,4] = min(369, 416, 228) = **228**  
→ s[1,4] = 3  

---

## Final Answer

Optimal cost:
→ **m[1,4] = 228**

Optimal split:
→ k = 3

---