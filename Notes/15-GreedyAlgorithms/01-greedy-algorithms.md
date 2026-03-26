# Greedy Algorithms

## Notes: Coin Change

### Goal
Return change (in cents) using the **minimum number of coins**

### Greedy Strategy
- Sort coins in descending order  
- Always pick the **largest available coin**

### Example 1: 52 cents

Coins: {25, 10, 5, 1}
Goal: 52 cents

Process:
- 52 − 25 = 27  
- 27 − 25 = 2  
- 2 − 1 = 1  
- 1 − 1 = 0  

Solution:
```text
25, 25, 1, 1