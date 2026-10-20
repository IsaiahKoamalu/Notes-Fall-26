## Sampling
![[Pasted image 20261020111106.png|193]]
- Suppose we want to find $p(C|W=\text{true})$
- Could compute exactly using variable elimination.
	- not practical for larger graphs
- We cannot sample from this distribution directly to get counts.
	- but we can sample from the joint distribution.

## Prior Sampling
- Generate a sample from the joint distribution w/o any evidence.
	- $x$  \~ $p(C,S,R,W)$
- Sample topological order $p(x_i|\text{Parents}(x_i))$
```
c = sample(Cloudy)        # [0.5, 0.5] -> true
s = sample(Sprinkler, c)  # [0.1, 0.9] -> false
r = sample(Rain, s)       # [0.8, 0.2] -> true
w = sample(Wet, s, r)     # [0.9, 0.1] -> true
```
- One sample: `(true, false, true, false)`
- After sampling, we get a table of samples.

| **C** | **S** | **R** | **W** |
| ----- | ----- | ----- | ----- |
| true  | false | true  | true  |
| false | false | false | true  |
| . . . | . . . | . . . | . . . |
- Can compute
	- unconditional: $p(C=\text{true})\approx\frac{\text{\# instances with }C=true}{\text{total instances}}$
	- conditional: 