# Activity Selection Problem

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/activityselection.png" alt="Activity Selection Problem" width="800" />
</p>

We are given a set of activities, each with:

- Start time: s<sub>i</sub>  
- Finish time: f<sub>i</sub>  

Goal: Select the **maximum number of non-overlapping activities.** <br>

Greedy Selection Rule: Select the activity that has the **earliest finish time.**

## Notes: Example

### Input

|    Activity   | s<sub>i</sub> | f<sub>i</sub> |
|---------------|---------------|---------------|
| a<sub>1</sub> | 6             | 8             |
| a<sub>2</sub> | 0             | 4             |
| a<sub>3</sub> | 4             | 7             |
| a<sub>4</sub> | 2             | 5             |

### Step 1: Sort by Finish Time

|    Activity   | s<sub>i</sub> | f<sub>i</sub> |
|---------------|---------------|---------------|
| a<sub>1</sub> | 0             | 4             |
| a<sub>2</sub> | 2             | 5             |
| a<sub>3</sub> | 4             | 7             |
| a<sub>4</sub> | 6             | 8             |

### Step 2: Greedy Selection Process

- Greedy Select: Pick first activity: a<sub>2</sub> (finishes at 4)
- a<sub>4</sub>: starts at 2 ❌ (overlaps with 4)
- a<sub>3</sub>: starts at 4 ✅ (compatible)
- a<sub>1</sub>: starts at 6 ✅ (but we already pick earlier compatible one first)

### Step 3: Build Solution

Selected activities:

```text
a2 → a3
```

## Notes: Proof of Optimality

We want to prove that the greedy choice is optimal: <b>Select the activity with the earliest finish time</b>

### Theorem 15.1

Consider any non-empty subproblem <b>S<sub>k</sub></b>.

Let <b>a<sub>m</sub></b> be the activity in <b>S<sub>k</sub></b> with the **earliest finish time**.

Then <b>a<sub>m</sub></b> is included in **some maximum-size subset of mutually compatible activities** in <b>S<sub>k</sub></b>. <br>

Even if we do not know the full optimal answer yet, we can safely choose the activity with the smallest finish time first because there exists an optimal solution that contains it. <br>

Let:

- <b>A<sub>k</sub></b> = a maximum-size subset of mutually compatible activities in <b>S<sub>k</sub></b>
- <b>a<sub>j</sub></b> = the activity in <b>A<sub>k</sub></b> that finishes earliest
- <b>a<sub>m</sub></b> = the activity in <b>S<sub>k</sub></b> with the earliest finish time overall

Because <b>a<sub>m</sub></b> finishes earlier than or at the same time as every other activity in <b>S<sub>k</sub></b>, we have:

<p>
  f<sub>m</sub> &le; f<sub>j</sub>
</p>

### Case 1: If a<sub>j</sub> = a<sub>m</sub>

If the earliest-finishing activity in the optimal solution is already <b>a<sub>m</sub></b>, then we are done.

That means <b>a<sub>m</sub></b> is already part of an optimal solution.

### Case 2: If a<sub>j</sub> &ne; a<sub>m</sub>

Now suppose the optimal solution <b>A<sub>k</sub></b> does **not** contain <b>a<sub>m</sub></b>.

<p>
  A<sub>k</sub><sup>'</sup> = A<sub>k</sub> - {a<sub>j</sub>} &cup; {a<sub>m</sub>}
</p>

- remove <b>a<sub>j</sub></b> from the optimal solution
- insert <b>a<sub>m</sub></b> instead

### Why Is A<sub>k</sub><sup>'</sup> Still Valid?

We need to show that the activities in <b>A<sub>k</sub><sup>'</sup></b> are still mutually compatible.

Since <b>a<sub>j</sub></b> was the activity in <b>A<sub>k</sub></b> with the earliest finish time, every other activity in <b>A<sub>k</sub></b> starts after <b>a<sub>j</sub></b> finishes.

So for every activity <b>a</b> that comes after <b>a<sub>j</sub></b> in <b>A<sub>k</sub></b>:

<p>
  s(a) &ge; f<sub>j</sub>
</p>

<p>
  f<sub>m</sub> &le; f<sub>j</sub>
</p>

<p>
  s(a) &ge; f<sub>j</sub> &ge; f<sub>m</sub>
</p>

So replacing <b>a<sub>j</sub></b> with <b>a<sub>m</sub></b> does **not** create any overlap.

That means <b>A<sub>k</sub><sup>'</sup></b> is still a compatible set.

### Why Is It Still Optimal?

The size of the new set does not change.

<p>
  |A<sub>k</sub><sup>'</sup>| = |A<sub>k</sub>|
</p>

So <b>A<sub>k</sub><sup>'</sup></b> has the same number of activities as the original optimal solution.

That means <b>A<sub>k</sub><sup>'</sup></b> is also an optimal solution.

And now it contains <b>a<sub>m</sub></b>.

### Conclusion

<p>
  \text{There exists an optimal solution that includes the earliest-finishing activity } a<sub>m</sub>
</p>

So choosing the activity with the earliest finish time is a **safe greedy choice**.

This proves the greedy-choice property for the Activity Selection Problem.


Once we choose the earliest-finishing activity, the remaining problem is:

- select the maximum number of compatible activities
- from those that start after the chosen activity finishes

This is the same kind of problem again, just smaller.

So the algorithm works by:

1. choosing the earliest-finishing activity
2. removing all incompatible activities
3. solving the remaining subproblem the same way

Because the greedy choice is always safe, repeating it leads to an optimal solution. <br>

The greedy algorithm for Activity Selection is optimal:
- Sort activities by finish time
- Repeatedly choose the next compatible activity with earliest finish time

