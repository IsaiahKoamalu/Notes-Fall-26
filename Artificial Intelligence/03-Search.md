## Pruning
- Idea: we do not actually need to explore the entire game tree

## Minimax with Alpha-Beta Pruning
- &alpha; and &beta; are bounds for the minimax value
- &alpha;: highest value choice so far for max

## Alpha-Beta Pruning
- Highly dependent on move ordering
- with optimal move order $O(b^m/2)$
	- reduces b to $\sqrt{b}$: 35  &rarr; 6 moves for chess
	- random is 

## Programming Chess
- Claude Shannon &rarr; Information Theory
- Strategies
	- Type A: explore all moves up to a certain depth, then use a heuristic
	- Type B: 

## Techniques
- **Cutoff**: do depth-limited minimax with alpha-beta pruning
	- heuristic evaluation function
	- quiescence search: if there is a pending move that can wildly swing the evaluation, do not cut it off.
- **Horizon Effect**: opponent facing inevitable destruction, but can find moves that allow survival past the search depth.
- **Forward Pruning**: prune moves that appear to be poor move.
- **Late Move Reduction**: Reduce move
- Lookup instead of search

## Heuristic Function

