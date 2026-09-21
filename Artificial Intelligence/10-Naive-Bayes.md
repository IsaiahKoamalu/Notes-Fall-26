## Graphical Model
- Probabilistic graphical model (PGM)
	- shows the causal relationship between variables
	- e.g. Meningitis causes stiff neck 70% of the time.
- **Bayesian Networks**: PGMs that are directed acyclic graphs (DAG)

## Recall
- Product rule: $p(ab)=p(a|b)p(b)=p(b|a)p(a)$
- Bayes' theorem/rule: $p(b|a)=\frac{p(ab)}{p(a)}=\frac{p(a|b)p(b)}{p(a)}$
- Why is this useful?
	- If we perceive an effect and want to find the cause.
		$\frac{p(\text{cause}|\text{effect})p(\text{cause})}{p(\text{effect})}$
	- where $p(\text{cause}|\text{effet})$ is the "diagnostic direction"
	- and $p(\text{effect}|\text{cause})$ is the "causal direction"

## Example
- A Doctor knows that:
	- Meningitis causes stiff neck 70% of the time
	- $1/50,000$ people have meningitis
	- $1/100$ people have stiff neck
- What is $p(m|s)$?
	- $p(m|s)=\frac{p(s|m)p(m)}{p(s)}=\frac{0.7*0.00002}{0.01}=0.0014$
- So you are not likely to have meningitis given that you have a stiff neck.

## Causal vs. Diagnostic
- Diagnostic knowledge is more fragile than causal knowledge.
- Suppose there is a meningitis epidemic
	- $p(m)$ will increase
	- causal: $p(s|m)$ doesn't change, still $0.7$
	- diagnostic: $p(m|s)$ will increase

## Multiple Variables
- 3 variables
	- cavity ($V$) causes toothache ($T$)
	- cavity ($V$) cause pick to catch ($C$)
- Are toothache and catch independent?
	- no, if the pick catches, then it is likely that you have a cavity which causes a toothache.
	- however, they are conditionally independent: if you know you have a cavity (or not), then the toothache does not directly cause the pick to catch, and vice versa.


## Conditional Independence
- Independence: $p(A,B)=p(A)p(B)$
- Conditional Independence: $p(T,C|V)=p(T|V)p(C|V)$

## Factoring
- Applying the product rule to factor the joint distribution: $p(T,C|V)=p(T|V)p(C|V)=p(T|V)p(C|V)p(V)$
- Why is this useful?
	- originally we had $2^3$ values in our joint distribution ($7$ independent numbers, since they have to sum to $1$)
	- factored, we need only $2+2+1$ independent numbers
		- $2\text{ x }2$ but each row sums to $1$
## Naive Bayes
- One cause directly influences multiple effects.
	$p(\text{cause},\text{effect}_1,\text{effect}_2,...)=p(\text{cause})\prod_{i}p(\text{effect}_i|\text{cause})$
- Simplifying assumption: conditional independence
	- often not true, but it makes the calculation much easier and works well in practice.
	

## Text Classification
- Given some text, assign a label.
	Input (some text) &rarr; [MODEL] &rarr; Output (A label)
	- Label could be: spam detection, authorship attribution, sentimnent analysis, language identification, hate speech detection

## Notation
- $x=$ the input, a vector of features
	- e.g.[I, am, Nigerian, prince, please, give, money]
- y = the label
	- e.g. spam
- Classification objective: find the best label
	$\hat{y} = \text{armgax}_{y \in Y} p(y|x)$
	- Much of ML is figuring out a good way to do this

## Interpretation
- Naive Bayes is a generative model
	- explicitly models the joint distribution $p(x,y)$
- Generative process: to generate an email
	- "Cause": select a label $y$ with some probability $p(y)$
	- "Effect": select words $x_1...x_n$ to include in the email based on probability $p(x_i|y)$

## Training a Naive Bayes Classifier
- Just counting
	$p(y)=\frac{\text{\# examples labeled y}}{\text{total \# of examples}}$
	$p(\text{word}|y=\frac{\text{\# number of times word appears in a y-labeled example}}{\text{total \# of words in y-labeled example}}$
	$\hat{y}=\text{argmax}_y p(y|x)$
	$=\text{argmax}_y \frac{p(x|y)p(y)}{p(x)}$
	$=\text{argmax}_yp(y)\prod_ip(x_i|y)$
- Note: the denominator disappears.