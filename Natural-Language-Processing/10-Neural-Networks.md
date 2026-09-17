## Biological Neuron
- Dendrites: receive input.

## McCulloch-Pitts Neuron
- Sum of inputs
	- Activation function: "fires" if the input reaches a threshold.

## Perceptron
- Linear function: $wx+b$ (constant bias term)
- Actually implemented as a machine.
- $(x_1, x_2, x_3, 1) (w_1, w_2, w_3, b) \sum z$

## Modern Neuron
- Same structure as a perceptron
	- new activation functions
	- new optimization algorithms

## $wx + b$ is a Neuron

## Note on Parameters
- No big difference between $w$ and $b$, they are just parameters.

## Piecewise Linear Function
- $f(x)=\phi_o + \phi_1x$ is  a bit limiting (just a straight line).
- Intuition: $wx+b$ defines a line
	- so combine multiple of them
	- replace $x$ in $f(x)=\phi_o + \phi_1x$ with two more lines
		- $f(x)=\phi_o + \phi_1(\phi_2 + \phi_3x) + \phi_4(\phi_5 + \phi_6x)$
- However: the combination of linear functions is still linear.
- Need a way to introduce non-linearity into functions.

## ReLU
- Rectified Linear Unit: an activation function
	- a neuron fires or activates if there is enough input
	- purpose: introduce non-linearity into the model