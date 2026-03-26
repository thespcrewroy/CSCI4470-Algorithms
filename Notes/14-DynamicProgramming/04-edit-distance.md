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
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/recursiveeditdistance.png" alt="Recursive Edit Distance DP" width="800" />
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
- Fill first row and first column using gap penalty (+1):
  - dp[0][j] = j  
  - dp[i][0] = i  
- Look at the **inverse “L” shape** of the cell you are at, and choose the minimum out of that for the cell:
  - left (insert)
  - top (delete)
  - diagonal (replace/match)

### Cost Table f[i,j]

|   | A | B | C | A | B |
|---|---|---|---|---|---|
|   | X | 1 | 2 | 3 | 4 | 5 |
| E | X | 1 | 2 | 3 | 4 | 5 |
| A | 2 | X | X | 3 | 3 | 4 |
| C | 3 | 2 | 2 | X | X | 4 |
| B | 4 | 3 | 2 | 3 | 3 | X |

**Edit Distance = 3**

- Move **diagonal** → match / replace  
- Move **left** → delete  
- Move **up** → insert  

- Follow direction of minimum value
- Edit distance doesn’t always give one unique solution

### Final Selection

1. Match B. Cost is +0
2. Delete A. Cost is +1
3. Match C. Cost is +0
4. Delete B. Cost is +1
5. Match A. Cost is +0
6. Insert E. Cost is +1

## Homework: Bottom Up Approach

(30 points) Consider the Edit Distance problem where edit operations have a cost and the goal is to **maximize editing score** in which matches are awarded positive scores.

Consider editing between the two strings:

S1 = DISTANCE  
S2 = DESTINY  

Scoring:
- Match = +4  
- Insert = -2  
- Delete = -2  
- Mismatch (replace) = -4  

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/newrule.png" alt="New f[i,j] formula" width="800" />
</p>


|   | D | I | S | T | A | N | C | E |
|---|---|---|---|---|---|---|---|---|
|   | 0 | -2 | -4 | -6 | -8 | -10 | -12 | -14 | -16 |
| D | -2 | 4 | 2 | 0 | -2 | -4 | -6 | -8 | -10 |
| E | -4 | 2 | 0 | -2 | -4 | -6 | -8 | -10 | -4 |
| S | -6 | 0 | -2 | 4 | 2 | 0 | -2 | -4 | -6 |
| T | -8 | -2 | -4 | 2 | 8 | 6 | 4 | 2 | 0 |
| I | -10 | -4 | 2 | 0 | 6 | 4 | 2 | 0 | -2 |
| N | -12 | -6 | 0 | -2 | 4 | 2 | 8 | 6 | 4 |
| Y | -14 | -8 | -2 | -4 | 2 | 0 | 6 | 4 | 2 |

### Table Creation

- Fill first row and column using gap penalty (-2)
 - dp[0][j] = -2j  
  - dp[i][0] = -2i   
- Look at the **inverse “L” shape** of the cell you are at, and choose the maximum of that for the cell:
  - left → insert (-2)
  - top → delete (-2)
  - diagonal → match (+4) or mismatch (-4)

### Cost Table f[i,j]


## Notes: Top Down Approach

```
Convert: DOG -> DIG

(DOG, DIG)
|
`-- Match G -> (DO, DI)
    |
    |-- Replace O -> I -> (DI, DI)
    |   `-- Match I -> (D, D)
    |       `-- Match D -> ("", "")  [base case]
    |
    |-- Insert I -> (DOI, DI)
    |   `-- Match I -> (DO, D)
    |       |
    |       |-- Insert D -> (DOD, D)
    |       |   `-- Match D -> (DO, "")  [dead end]
    |       |
    |       |-- Replace O -> D -> (DD, D)
    |       |   `-- Match D -> (D, "")  [dead end]
    |       |
    |       `-- Delete O -> (D, D)
    |           `-- Match D -> ("", "")  [base case]
    |
    `-- Delete O -> (D, DI)
        |
        |-- Insert I -> (DI, DI)
        |   `-- Match I -> (D, D)
        |       `-- Match D -> ("", "")  [base case]
        |
        |-- Delete D -> ("", DI)
        |   `-- [dead end]
        |
        `-- Replace D -> I -> (I, DI)
            `-- Match I -> ("", D)
                `-- [dead end]
```