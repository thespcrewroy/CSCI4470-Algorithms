# Matrix Chain Multiplication

## Notes: Matrix Chain Multiplication Problem

- Different parenthesizations (orders of multiplication) affect the total multiplication cost
- Matrix multiplication is associative  
    - (A1 A2) A3 = A1 (A2 A3)  
    - Both give the same result, but the cost (number of multiplications) changes depending on the order

**Goal: Find the parenthesization that minimizes the total number of scalar multiplications**

## Slides: Matrix Chain Multiplication – Cost Calculation

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/costanalysis.png" alt="Cost Analysis Example" width="800" />
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
- Case 1 is **10× faster.**
- Considerable savings can be achieved.
- Optimization goal: Choose the order that minimizes total scalar multiplications


## Notes: Dynamic Programming Recursive Solution

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/recursivematrixchain.png" alt="Recursive Formula" width="800" />
</p>

| Term | Meaning |
|------|--------|
| A_i ... A_j | The chain of matrices from i to j |
| k | The position where we split the chain |
| cost(A_i ... A_k) | Optimal cost of multiplying the left subchain |
| cost(A_{k+1} ... A_j) | Optimal cost of multiplying the right subchain |
| p_{i-1} p_k p_j | Cost of multiplying the two resulting matrices |
| min | Choose the split k that gives the smallest total cost |

1. Characterize the structure of the optimal solution
    * A<sub>i</sub> = (p<sub>i-1</sub>)(p<sub>i</sub>) in `<p1, p2, p3, ..., pn>`
    * A<sub>i...j</sub> = (A<sub>i</sub>)(A<sub>k</sub>)(A<sub>k+1</sub>)(A<sub>k+2</sub>)...(A<sub>j</sub>)
    * dim(A<sub>i...j</sub>) = (p<sub>i-1</sub>)(<sub>j</sub>)
2. Recursively defined m[i,j] as the minimum number of multiplications to compute A<sub>i...j</sub>
    * Assume the outermost parentheses occur between  A<sub>k</sub> and  A<sub>k+1</sub> 
    * k = parenthesis placement that goes over the range from `i` to `j - 1`
    * (A<sub>i...k</sub>)(A<sub>k+1 ... j</sub>) takes (p<sub>i-1</sub>)(p<sub>k</sub>)(p<sub>j</sub>) multiplications
3. Find the optimal parenthesizing for A<sub>1...k</sub> and A<sub>k+1 ... n</sub>
    * Consult the table of previously evaluated optimal sequences
    * Each entry in the table is evaluated the same way

### Paranthesizing: Splitting the Term
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


### Base Case A<sub>i</sub>

- m[1,1] = **0**
- m[2,2] = **0**  
- m[3,3] = **0**  
- m[4,4] = **0**  
    
### Compute A<sub>i</sub>A<sub>i+1</sub>

- m[1,2] = **216**; s[1,2] = **1**
    - i = 1; k = 1; j = 2 => min[1,1] + min[2,2] + (p<sub>0</sub>)(p<sub>1</sub>)(<sub>2</sub>) = 0 + 0 + (3)(9)(8) = 216
        - s[1,2] = 1
- m[2,3] = **144**; s[2,3] = **2**
    -  i = 2; k = 2; j = 3 => min[2,2] + min[3,3] + (p<sub>1</sub>)(p<sub>2</sub>)(p<sub>3</sub>) = 0 + 0 + (9)(8)(2) = 144  
        - s[2,3] = 2  
- m[3,4] = **80**; s[3,4] = **3**
    - i = 3; k = 3; j = 4 => min[3,3] + m[4,4] + (p<sub>2</sub>)(p<sub>3</sub>)(p<sub>4</sub>) = 0 + 0 + (8)(2)(5) = 80  
        - s[3,4] = 3  


### Compute A<sub>i</sub>A<sub>i+1</sub>A<sub>i+2</sub>

- m[1,3] = min(198, 264) = **198**; s[1,3] = **1**
    - i = 1; k = 1; j = 3 => m[1,1] + m[2,3] + (p<sub>0</sub>)(p<sub>1</sub>)(p<sub>3</sub>) = 0 + 144 + (3)(9)(2) = 198
        - s[1,3] = 1
    - i = 1; k = 2; j = 3 => m[1,2] + m[3,3] + (p<sub>0</sub>)(p<sub>2</sub>)(p<sub>3</sub>) = 216 + 0 + (3)(8)(2) = 264
        - s[2,3] = 2
- m[2,4] = min(440, 234) = **234**; s[2,4] = **3**
    - i = 2; k = 2; j = 4 => m[2,2] + m[3,4] + (p<sub>1</sub>)(p<sub>2</sub>)(p<sub>4</sub>) = 0 + 80 + (9)(8)(5) = 440
        - s[2,4] = 2
    - i = 2; k = 3; j = 4 => m[2,3] + m[4,4] + (p<sub>1</sub>)(p<sub>3</sub>)(p<sub>4</sub>) = 144 + 0 + (9)(2)(5) = 234
        - s[3,4] = 3

### A<sub>i</sub>A<sub>i+1</sub>A<sub>i+2</sub>A<sub>i+3</sub>

- m[1,4] = min(369, 416, 228) = **228**; s[1,4] = **3**
    - i = 1; k = 1; j = 4 = m[1,1] + m[2,4] + (p<sub>0</sub>)(p<sub>1</sub>)(p<sub>4</sub>) = 0 + 234 + (3)(9)(5) = 369
        - s[1, 4] = 1
    - i = 1; k = 2; j = 4 = m[1,2] + m[3,4] + (p<sub>0</sub>)(p<sub>2</sub>)(p<sub>4</sub>) = 216 + 80 + (3)(8)(5) = 416
        - s[2, 4] = 2
    - i = 1; k = 3; j = 4 = m[1,3] + m[4,4] + (p<sub>0</sub>)(p<sub>3</sub>)(p<sub>4</sub>) = 198 + 0 + (3)(2)(5) = 228
        - s[3,4] = 3

### Cost Table m[i,j]

| i \ j | 1   | 2   | 3   | 4   |
|------|-----|-----|-----|-----|
| 1    | 0   | 216 | 198 | 228 |
| 2    |     | 0   | 144 | 234 |
| 3    |     |     | 0   | 80  |
| 4    |     |     |     | 0   |

**Optimal Cost: 228**

### Selection Table s[i,j]

| i \ j | 1 | 2 | 3 | 4 |
|------|---|---|---|---|
| 1    | - | 1 | 1 | 3 |
| 2    |   | - | 2 | 3 |
| 3    |   |   | - | 3 |
| 4    |   |   |   | - |

- (A1 A2 A3 A4)
- s[1,4] = 3 → (A1 A2 A3) / A4 
- s[1,3] = 1 → (A1 / (A2 A3)) A4 
- s[2,3] = 2 → (A1 (A2 / A3)) A4 

**Optimal Parenthesization: ((A1 (A2 A3)) A4)**

## Homework: Bottom Up Approach

### Input

p = {9, 3, 8, 2, 5, 6}

Matrices:
- A1 = 3 × 9
- A2 = 9 × 8
- A3 = 8 × 2
- A4 = 2 × 5
- A5 = 5 x 6

Goal:
→ Compute m[1,5]

### Base Case A<sub>i</sub>

- m[1,1] = **0**
- m[2,2] = **0**  
- m[3,3] = **0**  
- m[4,4] = **0**  
- m[5,5] = **0**

### Compute A<sub>i</sub>A<sub>i+1</sub>

- m[1,2] = **216**; s[1,2] = **1**
    - i = 1; k = 1; j = 2 => min[1,1] + min[2,2] + (p<sub>0</sub>)(p<sub>1</sub>)(<sub>2</sub>) = 0 + 0 + (9)(3)(8) = 216
        - s[1,2] = 1
- m[2,3] = **48**; s[2,3] = **2**
    -  i = 2; k = 2; j = 3 => min[2,2] + min[3,3] + (p<sub>1</sub>)(p<sub>2</sub>)(p<sub>3</sub>) = 0 + 0 + (3)(8)(2) = 48 
        - s[2,3] = 2  
- m[3,4] = **80**; s[3,4] = **3**
    - i = 3; k = 3; j = 4 => min[3,3] + m[4,4] + (p<sub>2</sub>)(p<sub>3</sub>)(p<sub>4</sub>) = 0 + 0 + (8)(2)(5) = 80  
        - s[3,4] = 3  
- m[4,5] = **60**; s[4,5] = **4**
    - i = 4; k = 4; j = 5 => min[4,4] + min[5,5] + (p<sub>3</sub>)(p<sub>4</sub>)(p<sub>5</sub>) = 0 + 0 + (2)(5)(6) = 60
        - s[4,5] = 4

### Compute A<sub>i</sub>A<sub>i+1</sub>A<sub>i+2</sub>

- m[1,3] = min(102, 360) = **102**; s[1,3] = **1**
    - i = 1; k = 1; j = 3 => m[1,1] + m[2,3] + (p<sub>0</sub>)(p<sub>1</sub>)(p<sub>3</sub>) = 0 + 48 + (9)(3)(2) = 102
        - s[1,3] = 1
    - i = 1; k = 2; j = 3 => m[1,2] + m[3,3] + (p<sub>0</sub>)(p<sub>2</sub>)(p<sub>3</sub>) = 216 + 0 + (9)(8)(2) = 360
        - s[2,3] = 2
- m[2,4] = min(200, 78) = **78**; s[2,4] = **3**
    - i = 2; k = 2; j = 4 => m[2,2] + m[3,4] + (p<sub>1</sub>)(p<sub>2</sub>)(p<sub>4</sub>) = 0 + 80 + (3)(8)(5) = 200
        - s[2,4] = 2
    - i = 2; k = 3; j = 4 => m[2,3] + m[4,4] + (p<sub>1</sub>)(p<sub>3</sub>)(p<sub>4</sub>) = 48 + 0 + (3)(2)(5) = 78
        - s[3,4] = 3
- m[3,5] = min(156,320) = **156**; s[3,5] = 3
    - i = 3; k = 3; j = 5 => m[3,3] + m[4,5] + (p<sub>2</sub>)(p<sub>3</sub>)(p<sub>5</sub>) = 0 + 60 + (8)(2)(6) = 156
        - s[3,5] = 3
    - i = 3; k = 4; j = 5 => m[3,4] + m[5,5] + (p<sub>2</sub>)(p<sub>4</sub>)(p<sub>5</sub>) = 80 + 0 + (8)(5)(6) = 320
        - s[4,5] = 4

### Compute A<sub>i</sub>A<sub>i+1</sub>A<sub>i+2</sub>A<sub>i+3</sub>

- m[1,4] = min(213, 656, 192) = **192**; s[1,4] = **3**
    - i = 1; k = 1; j = 4 => m[1,1] + m[2,4] + (p<sub>0</sub>)(p<sub>1</sub>)(p<sub>4</sub>) = 0 + 78 + (9)(3)(5) = 213
        - s[1,4] = 1
    - i = 1; k = 2; j = 4 => m[1,2] + m[3,4] + (p<sub>0</sub>)(p<sub>2</sub>)(p<sub>4</sub>) = 216 + 80 + (9)(8)(5) = 656
        - s[1,4] = 2
    - i = 1; k = 3; j = 4 => m[1,3] + m[4,4] + (p<sub>0</sub>)(p<sub>3</sub>)(p<sub>4</sub>) = 102 + 0 + (9)(2)(5) = 192
        - s[1,4] = 3
- m[2,5] = min(300, 144, 168) = **144**; s[2,5] = **3**
    - i = 2; k = 2; j = 5 => m[2,2] + m[3,5] + (p<sub>1</sub>)(p<sub>2</sub>)(p<sub>5</sub>) = 0 + 156 + (3)(8)(6) = 300
        - s[2,5] = 2
    - i = 2; k = 3; j = 5 => m[2,3] + m[4,5] + (p<sub>1</sub>)(p<sub>3</sub>)(p<sub>5</sub>) = 48 + 60 + (3)(2)(6) = 144
        - s[2,5] = 3
    - i = 2; k = 4; j = 5 => m[2,4] + m[5,5] + (p<sub>1</sub>)(p<sub>4</sub>)(p<sub>5</sub>) = 78 + 0 + (3)(5)(6) = 168
        - s[2,5] = 4

### Compute A<sub>i</sub>A<sub>i+1</sub>A<sub>i+2</sub>A<sub>i+3</sub>A<sub>i+4</sub>
- m[1,5] = min(306, 804, 270, 462) = **270**; s[1,5] = **3**
    - i = 1; k = 1; j = 5 => m[1,1] + m[2,5] + (p<sub>0</sub>)(p<sub>1</sub>)(p<sub>5</sub>) = 0 + 144 + (9)(3)(6) = 306
        - s[1,5] = 1
    - i = 1; k = 2; j = 5 => m[1,2] + m[3,5] + (p<sub>0</sub>)(p<sub>2</sub>)(p<sub>5</sub>) = 216 + 156 + (9)(8)(6) = 804
        - s[1,5] = 2
    - i = 1; k = 3; j = 5 => m[1,3] + m[4,5] + (p<sub>0</sub>)(p<sub>3</sub>)(p<sub>5</sub>) = 102 + 60 + (9)(2)(6) = 270
        - s[1,5] = 3
    - i = 1; k = 4; j = 5 => m[1,4] + m[5,5] + (p<sub>0</sub>)(p<sub>4</sub>)(p<sub>5</sub>) = 192 + 0 + (9)(5)(6) = 462
        - s[1,5] = 4

### Cost Table m[i,j]

| i \ j | 1   | 2   | 3   | 4   | 5   |
|------|-----|-----|-----|-----|-----|
| 1    | 0   | 216 | 102 | 192 | 270 |
| 2    |     | 0   | 48  | 78  | 144 |
| 3    |     |     | 0   | 80  | 156 |
| 4    |     |     |     | 0   | 60  |
| 5    |     |     |     |     | 0   |

**Optimal Cost: 270**

### Selection Table s[i,j]

| i \ j | 1 | 2 | 3 | 4 | 5 |
|------|---|---|---|---|---|
| 1    | - | 1 | 1 | 3 | 3 |
| 2    |   | - | 2 | 3 | 3 |
| 3    |   |   | - | 3 | 3 |
| 4    |   |   |   | - | 4 |
| 5    |   |   |   |   | - |

- (A1 A2 A3 A4 A5)
- s[1,5] = 3 → (A1 A2 A3) / (A4 A5)
- s[1,3] = 1 → (A1 / (A2 A3)) (A4 A5)
- s[2,3] = 2 → (A1 (A2 / A3)) (A4 A5)
- s[4,5] = 4 → (A1 (A2 A3)) (A4 / A5)

**Optimal Parenthesization: ((A1 (A2 A3)) (A4 A5))**


The table below is a selection table for Matrix Chain Multiply. The table is not turned sideways as the book does it. What is the optimal parenthesizing for this matrix chain?

## Quiz: Parenthesizing

### Selection Table s[i,j]

| i \ j | 1 | 2 | 3 | 4 | 5 | 6 |
|------|---|---|---|---|---|---|
| 1    | - | 1 | 1 | 3 | 1 | 3 |
| 2    |   | - | 2 | 3 | 3 | 3 |
| 3    |   |   | - | 3 | 3 | 3 |
| 4    |   |   |   | - | 4 | 5 |
| 5    |   |   |   |   | - | 5 |
| 6    |   |   |   |   |   | - |

- (A1 A2 A3 A4 A5 A6)
- s[1,6] = 3 → (A1 A2 A3) / (A4 A5 A6)
- s[1,3] = 1 → (A1 / (A2 A3)) (A4 A5 A6)
- s[2,3] = 2 → (A1 (A2 / A3)) (A4 A5 A6)
- s[4,6] = 5 → (A1 (A2 A3)) ((A4 A5) / A6)
- s[4,5] = 4 → (A1 (A2 A3)) ((A4 / A5) A6)

**Optimal Parenthesization: ((A1 (A2 A3)) ((A4 A5) A6))**