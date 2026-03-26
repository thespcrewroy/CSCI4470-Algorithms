# Matrix Chain Multiplication

## Notes: Matrix Chain Multiplication Problem

- Different parenthesizations (orders of multiplication) affect the total multiplication cost
- Matrix multiplication is associative  
    - (A1 A2) A3 = A1 (A2 A3)  
    - Both give the same result, but the cost (number of multiplications) changes depending on the order

**Goal: Find the parenthesization that minimizes the total number of scalar multiplications**