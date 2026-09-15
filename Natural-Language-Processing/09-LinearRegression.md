## 1D Linear Regression
- Task: given $x$, predict$y$
- Model: a function $f$ that maps $x$ to $y$
- $f(x) = mx+b$
## Some Terminology
- Linear model $f(x)=wx+b$
	- $w$ is the weight: how much does $x$ contribute
	- $b$ is the bias/intercept: shifts the whole line
- Model parameters: variables internal to the model that affect the output
- Training/learning/fitting: find the best parameters
- Once we find the best, then for any given x we can perform inference
- What is best? Gives the best perfomance.
	- Loss function: measures how off we are from the correct answer.

## First Loss Function
- Squared loss
- Properties:
	- bigger is worse
	- do not care if prediction is bigger or smaller, just the difference (so square it)
	- does not matter which term comes first
- Notes:
	- common variant ...
	- should be written as ...