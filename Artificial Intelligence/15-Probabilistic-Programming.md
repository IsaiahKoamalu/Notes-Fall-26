## Example: Coin Tossing
- Suppose we have some coin flip counts
- Don't know the weight of the coin
- Frequentist Inference: just count and normalize
```python
flips = [0, 1, 1, 0, 0, 1, 1, 1, 1, 0, 0, 1, 1, 0, 1, 0, 0]  
obs = sum(flips)  
n = len(flips)  
p = obs / n # 0.55
```
**Bayesian inference:** choose a model.
- Define the likelihood function &rarr; how likely is the data given some parameters.
- Bernoulli distribution &rarr; for $n$ independent Bernoulli trials with probablility $p$.
	$\text{obs}$ ~ $\text{Binomial}(n, p)$  
## Convergence Checks
- Run MCMC to find p(parameters | obs)
	- probability of parameters given observations.
- `n_eff`: effective samples (should be high)
- Gelmin-Rubin statistic `r_hat`: should be close to 1
- Divergences: if the chain has diverged

## Trace Plot
- Shows the samples and their distributions
	- Multiple chains
	- 