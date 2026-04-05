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
<p>
  <strong>1.</strong>
  Totaltime(i) =
  min
  &Sigma;<sub>j=1</sub><sup>n</sup>
  &Sigma;<sub>c=1</sub><sup>j-1</sup>
  ServiceTime(i) + ServiceTime(j)
</p>

<p>
  <strong>2.</strong>
  min
  &Sigma;<sub>i=1</sub><sup>n</sup>
  (n - i + 1)t<sub>i</sub>
</p>