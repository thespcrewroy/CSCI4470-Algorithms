# Greedy Algorithms

## Notes: Coin Change Example

### Goal
Return change (in cents) using the **minimum number of coins**

### Greedy Strategy
- Sort coins in descending order  
- Always pick the **largest available coin**

### Example: 52 cents

Coins: {25, 10, 5, 1}
Goal: 52 cents

Process:
- 52 − 25 = 27  
- 27 − 25 = 2  
- 2 − 1 = 1  
- 1 − 1 = 0  

```text
Output = {25, 25, 1, 1}
```

**This is the global optimal solution.**

### Counter Example: 16 cents

**Greedy works only if local optimal choices lead to global optimal solution.**
- Greedy = pick best local choice
- Works only when problem has greedy-choice property
- Otherwise, need Dynamic Programming

Coins: {10, 7, 1}
Goal: 16 cents

Greedy Process:
- 16 - 10 = 6
- 6 - 1 = 5
- 5 - 1 = 4
- 4 - 1 = 3
- 3 - 1 = 2
- 2 - 1 = 1
- 1 - 1 = 0

```text
Output = {10, 1, 1, 1, 1, 1, 1}
```

**This is NOT the global optimal solution.**

**The optimal solution is actually: {7, 7, 1, 1}**

- Greedy is fast and simple, but not always correct
- Always verify: oes greedy lead to global optimal?