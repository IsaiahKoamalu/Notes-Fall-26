#### Previously
- Build a model.
- Design a loss function.
- Optimize model parameters.
- Today: do it all in PyTorch
	- full ML workflow

#### Workflow
- Load data
- Preprocess data
- Define model
- Choose loss function and optimizer
- Run training loop

#### PyTorch ?
- Deep learning framework for Python
	- like NumPy, but operations can be executed on the GPU
- Why GPU
	- thousands of cores specialized for certain operations
	- run in parallel

#### Tensor
- Pytorch tensor is likfe NumPy ndarray
- Can keep track of gradients when performing operations.
```Python
```

#### Data
- Wrap data in a Dataset class
	- must define `__len__` and `__getitem__` (operator overloading)
- Why?
	- standard APO
	- Entire data may not fit on your GPU
		- load it as you go
	- can preprocess data here
```Python
```

#### Preprocessing
- Backprop works better with small numbers
- Standardize data (z-score)
	- subtract mean, divide by stdev
	- "zero mean, unit variance"
```Python
```

#### Dataloader
- Allows you to iterate through the dataset
- Handy features
	- batching: run multiple inputs at the same time
	- shuffling: remove dependence on the ordering.
```Python
```

#### Layers
- Linear is $wx+b$
	- weights has size (out, in)
	- randomly initialized
```Python
```
- Sequential runs multiple layers in sequence
	- ReLU is also a layer
```Python
```

#### Model
- Create your own model by inheriting from `torch.nn.Module`
- `forward()` is the forward pass
- `__call__` already defined.
```Python
```

#### Training Loop
- For one epoch (one pass through the data)
- Looping through the dataloader by batch.
```Python
```
- Train for multiple epochs
```Python
```
- How do you choose how many epochs?

#### Validation Set
- Instead of train/test splits, have three splits.
- Train (homework), Val (quiz), Test (exam).
- Goal: generalization (does well on train and test)

#### Training Loop with Early Stopping
- Early stopping: stop training if val loss does not improve after a certain number of epochs (patience).
```Python
```
