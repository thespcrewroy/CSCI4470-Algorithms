# Ford-Fulkerson Algorithm

1. Initialize flow `f` to 0
2. While for each augmenting path `p` in the residual network `G_f = {V, E}`
3. Augement flow `f` along path `p`
4. return `f`

## Notes: Residual Network

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/ford.png" alt="Ford Fulkerson" width="400" 
/>

- Tells you the remaining capacity left to increase the flow