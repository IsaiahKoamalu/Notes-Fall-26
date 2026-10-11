- **So far:** given ($x,y$) pairs, find the best model $f(x)$

## New Way of Thinking
- Where did $y$ come from?
	- generated from some distribution (generative process)
- We should model the conditional probability distribution.
- Assume a probability that generates $y$.
- Set your model to predict one or more parameters.
- Generate the most likely point $y$ from the distribution.
## Optimization
- Old thinking: find the parameters that minimize the loss.
- New thinking: find the parameters

## Assumptions
- A bit unwieldy
- Assumption 1: each data point is independent
- Assumption 2: the distributions that generate each $y_i$ have the same form.
- Together: independent and identically distributed.
## Optimization
- Goal: maximize the likelihood of the data
- Maximum likelihood criterion.
## Maximum Likelihood