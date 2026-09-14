- Search Problems: find a path to a goal
- Optimization Problems: find the best state
- Constraint Satisfaction: find a solution that satisfies some constraints
	- doesn't matter how we get there

## Formally
- A set of variables {$X_1, X_2, ...$}
- A domain for each variable {$D_1, D_2, ...$}
	- A set of allowable values, or a range [lb, ub]
- A set of constraints {$<\text{scope}_1, \text{rel}_1>, ...$}
	-  e.g. $<(X_1, X_2)., X_1 > X_2$

## Graph Coloring
- Task: assign a color (R/G/B) to each state/territory such that no adjacent ones have the same color.
```
Variables:  
X = {WA, NT, Q, NSW, V, SA, T}  

Domain:  
WA, NT, Q, ... {R,G,B}∈  

Constraints:  
C = {  
	SA≠WA, SA≠NT, SA≠Q, SA≠NSW, SA≠V,  
	WA≠NT, NT≠Q, Q≠NSW, NSW≠V
}
```

## CSPs
- Discrete, finite domain
	- graph coloring
	- n-queens
	- sudoku
	- 0-1 knapsack
- Continuous
	- planting wheat vs. corn
	- swimming times

## Types of Constraints
- Unary constraint: just one variable
	- WA $\not =$ green
- Binary constraint: two variables
	- WA $\not =$ SA
- Global constraint: can involve many variables
	- Alldiff: all variables in the constraint have to be different.
- Linear constraint: constraint is a linear combination
	- $2*\text{wheat}+3*\text{corn}<50$
	- can be solved in polynomial time (nonlinear NP is hard)

## Constraints
- Cryptarithmetic puzzles
	- ```
			  CP
		+	  IS
		+	  FUN
		----------
		=	  TRUE
	  ```
- Constraint hypergraph: encodes which constraints are in effect for which variables.
## Solving CSPs
- First attempt: try DFS
- Problem: DFS reaches a base case before discovering an invalid assignment.
- Backtracking: specialized DFS algorithm
	- build partial assignments incrementally
	- abandon them as soon as a constraint is violated

## Variable Ordering
- How to choose the next unassigned variable?
	- go in order
	- random
- Minimum-Remaining-Values (MRV) heuristic
	-  choose the variable with the fewest legal values remaining (tries to fail fast)
- Degree heuristic
	- choose the variable involved in the most constraints with other unassigned variables
- Least-Constrained-Value heuristic
	- choose values that rule out the fewest choices

## Solving SCPs with Local Search
- Min-Conflicts-Heuristic: select a value that results in the minimum number of conflicts with other variables.

## Summary
- CSPs represent state with a set of {$\text{var}=\text{value}, ...$}
- Commonly solved with backtracking
- Heuristics for choosing which variable/value to try next.
- Fancier algorithms to rule out certain variable assignments.