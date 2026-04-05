# Minimizing the Total Time in the System

## Fractional Knapsack Problem
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/minimizingtime.png" alt="Fractional Knapsack Problem" width="800" />
</p>

## Slides: Example
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/minimizingtimeexample1.png" alt="Fractional Knapsack Problem" width="800" />
</p>

## Notes: Greedy Strategy

The optimal greedy choice is to serve the customer with the smallest service time first.

- Candidate set: all customers
- Selection function: pick the customer with minimum service time
- Feasibility function: any order is feasible
- Objective function: ```Total_Time(j) = Wait_Time(j) + Service_Time(j)```
- Solution function: all customers are scheduled

This is the same idea as shortest processing time first.

## Notes: Objective Function
<pre>
1) Totaltime(i) = min Σ(j=1 to n) Σ(c=1 to j-1) ServiceTime(i) + ServiceTime(j)

2) min Σ(i=1 to n) (n - i + 1)k_i
</pre>