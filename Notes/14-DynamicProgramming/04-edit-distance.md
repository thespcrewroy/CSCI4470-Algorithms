# Edit Distance

## Notes: Goal
Convert string **S1 to S2** using the **minimum number of operations**

## Notes: Allowed Operations
1. **Insert**
2. **Delete**
3. **Replace**

### Delete
Remove a character from S1  
- Example: "horse" → remove 'h' → "orse"

### Insert
Add a character to S1  
- Example: "horse" → insert 's' → "horses"

### Replace
Change one character in S1  
- Example: "horse" → replace 'e' with 's' → "horss"


## Notes: Dynamic Programming Recursive Solution

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/recursiveeditdistance.png" alt="Recursive Edit Distance DPy" width="800" />
</p>

## Notes: Bottom Up Approach

S1 = ABCAB  
S2 = EACB  

|   | A | B | C | A | B |
|---|---|---|---|---|---|
|   | 0 | 1 | 2 | 3 | 4 | 5 |
| E | 1 | 1 | 2 | 3 | 4 | 5 |
| A | 2 | 1 | 2 | 3 | 3 | 4 |
| C | 3 | 2 | 2 | 2 | 3 | 4 |
| B | 4 | 3 | 2 | 3 | 3 | 3 |

### Table Creation
- Fill first row and first column:
  - dp[0][j] = j  
  - dp[i][0] = i  
- Look at the **inverse “L” shape** of the cell you are at, and choose the minimum out of that for the cell:
  - left (insert)
  - top (delete)
  - diagonal (replace/match)