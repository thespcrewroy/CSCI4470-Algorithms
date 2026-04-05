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

## Notes: Proof of Optimality (BWOC)

We want to minimize the **total time in the system** for all customers/jobs.

Assume each customer has a service time:

<p>
  t<sub>1</sub>, t<sub>2</sub>, ..., t<sub>n</sub>
</p>

### Objective Function

The objective function is:

<p>
  TotalTime = min &Sigma;<sub>i=1</sub><sup>n</sup> (n - i + 1)t<sub>i</sub>
</p>

This means earlier jobs affect more total waiting time, so their position matters more.

### Greedy Choice

The greedy strategy is:

- Sort the service times in **increasing order**
- Serve the customer with the **smallest** service time first

So the intended order is:

<p>
  t<sub>1</sub> &le; t<sub>2</sub> &le; ... &le; t<sub>n</sub>
</p>


### Proof By Contradiction

We want to prove that serving customers in sorted order by smallest service time first is **optimal**. We use a **proof by contradiction**.


### Step 1: Assume an Optimal Solution That Is Not Sorted

Assume there exists an optimal solution that is **not** sorted.

That means there are two positions <b>a</b> and <b>b</b> such that:

<p>
  a &lt; b
</p>

but the service times are out of order:

<p>
  t<sub>a</sub> &gt; t<sub>b</sub>
</p>

So even though customer <b>a</b> comes before customer <b>b</b>, it has a larger service time.

### Step 2: Define the Two Solutions

Let:

<p>
  S<sub>1</sub> = t<sub>1</sub>, t<sub>2</sub>, ..., t<sub>a</sub>, t<sub>b</sub>, ..., t<sub>n</sub>
</p>

This is the assumed optimal solution, but it is not sorted.

Now swap the two out-of-order terms:

<p>
  S<sub>2</sub> = t<sub>1</sub>, t<sub>2</sub>, ..., t<sub>b</sub>, t<sub>a</sub>, ..., t<sub>n</sub>
</p>

The idea is to compare the objective values of <b>S<sub>1</sub></b> and <b>S<sub>2</sub></b>.

---

## Step 3: Write Only the Terms That Change

Swapping two jobs only changes the part of the objective function involving those two positions.

So for <b>S<sub>1</sub></b>, the relevant contribution is:

<p>
  Obj<sub>old</sub> = (n - a + 1)t<sub>a</sub> + (n - b + 1)t<sub>b</sub>
</p>

For <b>S<sub>2</sub></b>, after swapping:

<p>
  Obj<sub>new</sub> = (n - a + 1)t<sub>b</sub> + (n - b + 1)t<sub>a</sub>
</p>

---

## Step 4: Subtract the Two Objective Values

Now compute:

<p>
  Obj<sub>old</sub> - Obj<sub>new</sub>
</p>

Substitute the two expressions:

<p>
  Obj<sub>old</sub> - Obj<sub>new</sub> =
  ((n - a + 1)t<sub>a</sub> + (n - b + 1)t<sub>b</sub>)
  -
  ((n - a + 1)t<sub>b</sub> + (n - b + 1)t<sub>a</sub>)
</p>

Distribute and group like terms:

<p>
  = (n - a + 1)(t<sub>a</sub> - t<sub>b</sub>) + (n - b + 1)(t<sub>b</sub> - t<sub>a</sub>)
</p>

Factor:

<p>
  = ((n - a + 1) - (n - b + 1))(t<sub>a</sub> - t<sub>b</sub>)
</p>

Simplify:

<p>
  = (b - a)(t<sub>a</sub> - t<sub>b</sub>)
</p>

---

## Step 5: Show the Difference Is Positive

From the assumption:

<p>
  a &lt; b
</p>

so:

<p>
  b - a &gt; 0
</p>

Also from the inversion assumption:

<p>
  t<sub>a</sub> &gt; t<sub>b</sub>
</p>

so:

<p>
  t<sub>a</sub> - t<sub>b</sub> &gt; 0
</p>

Therefore:

<p>
  (b - a)(t<sub>a</sub> - t<sub>b</sub>) &gt; 0
</p>

So:

<p>
  Obj<sub>old</sub> - Obj<sub>new</sub> &gt; 0
</p>

which means:

<p>
  Obj<sub>old</sub> &gt; Obj<sub>new</sub>
</p>

---

## Step 6: Reach the Contradiction

But this is impossible.

We assumed <b>S<sub>1</sub></b> was an **optimal** solution.

Yet after swapping the out-of-order pair, we found a new solution <b>S<sub>2</sub></b> with a **smaller** objective value:

<p>
  Obj<sub>new</sub> &lt; Obj<sub>old</sub>
</p>

This contradicts the assumption that <b>S<sub>1</sub></b> was optimal.

---

## Final Conclusion

Therefore, an optimal solution cannot contain an out-of-order pair.

So the optimal ordering must be sorted:

<p>
  t<sub>1</sub> &le; t<sub>2</sub> &le; ... &le; t<sub>n</sub>
</p>

That proves the greedy rule:

- Always select the customer/job with the **smallest service time** first

---

## Why This Works

Earlier positions in the schedule get multiplied by larger coefficients:

<p>
  (n - i + 1)
</p>

So putting a large service time early increases the total time in the system more than putting it later.

That is why sorting by smallest service time first minimizes the objective function.

---

## Takeaway

- Objective:
  <p>
    min &Sigma;<sub>i=1</sub><sup>n</sup> (n - i + 1)t<sub>i</sub>
  </p>

- Greedy choice:
  serve jobs in increasing order of service time

- Proof idea:
  if an optimal solution is not sorted, swap an inverted pair

- Result:
  the swap lowers the objective function

- Contradiction:
  the original solution could not have been optimal

- Conclusion:
  **Shortest job first is optimal**

---

## Time Complexity

If we sort the jobs first:

```text
Sorting: O(n log n)
Scheduling after sorting: O(n)
Overall: O(n log n)