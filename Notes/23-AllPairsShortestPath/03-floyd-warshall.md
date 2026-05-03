# Floyd Warshall Algorithm

- Dynamic programming based solution
- Looks at all the intermediate vertices in the shortest path from v<sub>i</sub> to v<sub>j</sub>
- p<sub>ij</sub> = (v<sub>1</sub>, v<sub>2</sub>, ..., v<sub>k</sub>) (for k intermediate vertices)
- p<sub>ij</sub>: shortest path from v<sub>i</sub> to v<sub>j</sub>
- 2 Possibilities
  - If vertex v<sub>k</sub> is not part of the shortest path from v<sub>i</sub> to v<sub>j</sub>, then intermediate vertices are (v<sub>1</sub>, v<sub>2</sub>, ..., v<sub>k-1</sub>)
  - If vertex v<sub>k</sub> is part of the shortest path, then we go from v<sub>i</sub> to v<sub>k</sub>, and then from v<sub>k</sub> to v<sub>j</sub> (v<sub>i</sub> ... v<sub>k</sub>, v<sub>k</sub> ... v<sub>j</sub> )