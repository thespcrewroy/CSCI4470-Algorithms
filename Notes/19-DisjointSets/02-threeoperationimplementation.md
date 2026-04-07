# 3 Operation Implementation


## Notes: Make_Set(x) Example

2, 5, 7, 3  (input vertices)

- S<sub>1</sub> = Make_Set(2) = {2}   (rep = 2)
- S<sub>2</sub> = Make_Set(5) = {5}   (rep = 5)
- S<sub>3</sub> = Make_Set(7) = {7}   (rep = 7)
- S<sub>4</sub> = Make_Set(3) = {3}   (rep = 3) 

## Notes: Union(x) Example

- S<sub>5</sub> = Union(S<sub>2</sub> , S<sub>4</sub>) = {5, 3}       (rep = 5)
- S<sub>6</sub> = Union(S<sub>5</sub> , S<sub>1</sub>) = {5, 3, 2}    (rep = 5)

## Notes: Find_Set(x) Example
- S<sub>7</sub> = Find_Set(2) = 5     (rep = 5)
- S<sub>8</sub> = Find_Set(3) = 5     (rep = 5)
- S<sub>9</sub> = Find_Set(5) = 5     (rep = 5)
- S<sub>10</sub> = Find_Set(7) = 7    (rep = 7)

## Example: Finding Connected Components

### Graph

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/disconnected.png" alt="Disconnected Disjoint Set Graph" height="500" width="500" />
</p>

- Vertices: A, B, C, D, E, F, G  
- Edges: (A, B), (B, C), (C, D), (A, D), (E, F)

### Step 1: Make_Set on all vertices

{A}, {B}, {C}, {D}, {E}, {F}, {G}


### Step 2: Process Edges

#### Edge (A, B)

- Find_Set(A) = A  
- Find_Set(B) = B  
- Union() = {A, B}   (rep = A)

#### Edge (B, C)

- Find_Set(B) = A  
- Find_Set(C) = C  
- Union() = {A, B, C}   (rep = A)

#### Edge (C, D)

- Find_Set(C) = A  
- Find_Set(D) = D  
- Union() = {A, B, C, D}   (rep = A)

#### Edge (A, D)

- Find_Set(A) = A  
- Find_Set(D) = A  
- Same → ❌ no union

#### Edge (E, F)

- Find_Set(E) = E  
- Find_Set(F) = F  
- Union() = {E, F}   (rep = E)

### Step 3: List Out Connected Components

{A, B, C, D}, {E, F}, {G}

Number of Sets = Numeber of Components = **3**