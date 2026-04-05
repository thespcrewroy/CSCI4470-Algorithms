# Activity Selection Problem

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/activityselection.png" alt="Activity Selection Problem" width="800" />
</p>

We are given a set of activities, each with:

- Start time: s<sub>i</sub>  
- Finish time: f<sub>i</sub>  

Goal: Select the **maximum number of non-overlapping activities**

---

## Greedy Selection Rule

<p>
  Select the activity that has the <b>earliest finish time</b>
</p>

---

## Example 1

### Input

| Activity | s<sub>i</sub> | f<sub>i</sub> |
|----------|--------------|--------------|
| a<sub>1</sub> | 6 | 8 |
| a<sub>2</sub> | 0 | 4 |
| a<sub>3</sub> | 4 | 7 |
| a<sub>4</sub> | 2 | 5 |

---

## Step 1: Sort by Finish Time

| Activity | s<sub>i</sub> | f<sub>i</sub> |
|----------|--------------|--------------|
| a<sub>2</sub> | 0 | 4 |
| a<sub>4</sub> | 2 | 5 |
| a<sub>3</sub> | 4 | 7 |
| a<sub>1</sub> | 6 | 8 |

---

## Step 2: Greedy Selection Process

- Pick first activity: a<sub>2</sub> (finishes at 4)

Now check compatibility:

- a<sub>4</sub>: starts at 2 ❌ (overlaps with 4)
- a<sub>3</sub>: starts at 4 ✅ (compatible)
- a<sub>1</sub>: starts at 6 ✅ (but we already pick earlier compatible one first)

---

## Step 3: Build Solution

Selected activities:

```text
a2 → a3