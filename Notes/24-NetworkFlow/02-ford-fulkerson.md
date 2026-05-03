# Ford-Fulkerson Algorithm

1. Initialize flow `f` to 0
2. While for each augmenting path `p` in the residual network `G_f = {V, E}`
3. Augement flow `f` along path `p`
4. return `f`

## Notes: Residual Network

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/ford.png" alt="Ford Fulkerson" width="400" 
/>

<br>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/residual.png" alt="Resiudal Network" width="400" 
/>

*Tells you the remaining capacity left to increase the flow.*

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/back.png" alt="Ford Fulkerson Resid" width="400" 
/>

<br>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/back2.png" alt="Ford Fulkerson Resid" width="400" 
/>


- Example: E(s, w)
  - Flow: f(s, w) = 1
  - Capacity: c(s, w) = 3
  - Thus, we can forward the 2 residual units from `s` to `w`
  - Send the 1 flow unit back from `w` to `s`
- Example: E(w, x)
  - Flow: f(w, x) = 2
  - Capacity: c(w, x) = 2
  - No residual transition from `w` to `x`
  - Send the 2 flow unit back from `x` to `w`