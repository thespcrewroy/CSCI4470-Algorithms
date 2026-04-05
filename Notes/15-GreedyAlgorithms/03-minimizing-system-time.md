# Minimizing the Total Time in the System

## Fractional Knapsack Problem
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/minimizingtime.png" alt="Fractional Knapsack Problem" width="800" />
</p>

## Slides: Example
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/minimizingtimeexample1.png" alt="Fractional Knapsack Problem" width="800" />
</p>

## Problem Setup

We have a set of customers C1, C2, ..., Cn, and each customer i requires service time t_i.

If customers are processed in some order, then the total time in the system for customer j is:

TotalTime(j) = WaitingTime(j) + ServiceTime(j)

The goal is to choose an order that minimizes the total time spent in the system by all customers.

## Greedy Strategy

The optimal greedy choice is to serve the customer with the smallest service time first.

- Candidate set: all customers
- Selection function: pick the customer with minimum service time
- Feasibility function: any order is feasible
- Objective function: minimize the sum of all customers' total times in the system
- Solution function: all customers are scheduled

This is the same idea as shortest processing time first.

## Why It Works

If the service times are sorted in nondecreasing order:

t_1 <= t_2 <= ... <= t_n

then the total time in the system is:

TotalTime = sum from j = 1 to n of sum from i = 1 to j of t_i

which can be rewritten as:

TotalTime = sum from i = 1 to n of (n - i + 1) t_i

Because earlier service times affect more customers, the smallest service times should appear first.

## Example

Suppose the service times are:

- C1 = 5
- C2 = 10
- C3 = 3

### ❌ Original order: C1, C2, C3

Total time = 5 + (5 + 10) + (5 + 10 + 3)

Total time = 5 + 15 + 18 = 38

### ✅ Greedy order: C3, C1, C2

Sort by smallest service time first:

- C3 = 3
- C1 = 5
- C2 = 10

Total time = 3 + (3 + 5) + (3 + 5 + 10)

Total time = 3 + 8 + 18 = 29

So the greedy order gives the smaller total time in the system.

## Slides: Example
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/minimizingtimeexample1.png" alt="Minimizing the Total Time in the System Example" width="800" />
</p>