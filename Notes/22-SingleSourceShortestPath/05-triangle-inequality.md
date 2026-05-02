# Triangle Inequality Property

- Let source be `s`, with edge `(u, v)` &isin; E.
- The shortest-path distance is written as &delta;(x, y).
- Triangle inequality in shortest paths:
	- `&delta;(s, v) &le; &delta;(s, u) + w(u, v)`
- Why this is true (from the sketch):
	- Consider path `P1`: a shortest path from `s` to `v` with length `&delta;(s, v)`.
	- Consider path `P2`: go from `s` to `u` using a shortest path, then take edge `(u, v)`.
	- Length of `P2` is `&delta;(s, u) + w(u, v)`.
	- Since `P1` is shortest, `P1 &le; P2`.
	- Therefore, `&delta;(s, v) &le; &delta;(s, u) + w(u, v)`.
- Equality case:
	- If a shortest path from `s` to `v` ends with edge `(u, v)`, then
		`&delta;(s, v) = &delta;(s, u) + w(u, v)`.
- Strict inequality case:
	- If the best route to `v` does not go through `u`, then
		`&delta;(s, v) &lt; &delta;(s, u) + w(u, v)`.
- This property is the key justification for edge relaxation in shortest-path algorithms.

