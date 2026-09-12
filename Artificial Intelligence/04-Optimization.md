## Hill Climbing
- A local search algorithm
	- always head in the right direction
	- can get stuck
	```Python
	  def hill_climbing(problem):
		  current = problem.initial_state
		  while True:
			  neighbor = the highest successor state of current
			  if value(neighbor) <= value(current):
				  return current
			  current = neighbor
	```

## Local Search
- Benefits
	- does not keep track of the path, uses much less memory.
	- can find decent solutions
- Drawbacks
	- not complete - may not find the goal (global maximum)
	- could get stuck in local maxima or plateaus
		- need a way to move "sideways"

## Hill Climbing Variants
- Stochastic hill climbing: pick randomly from among the uphill moves
- Random restart hill climbing: multiple hill climbs starting from different random states.

## Simulated Annealing
- Combine hill climbing with random walks so you can sometimes go downhill.
- In metallurgy: heat a metal and let it cool, which alters the metal's properties.
- Switch from hill climbing (maximize) to gradient descent (minimize).
- Early in the search, it is okay to go up (away from goal)
```Python
	def simulated_annealing(problem, schedule):
		current = problm.initial_state
		for t in range(1, infinity):
			T  = schedule(t) # temperature
			if T == 0:
				return current
			next = randomly selected successor of current
			delta_E = value(current) - value(next)
			if delta_E > 0:
				current = next
			else: # accept with decresing probability
				current = next with probability e^(-delta_E/T)
```

## Local Beam Search
- Keep k best current states at each iteration
```Python
	def local_beam_search(problem, k):
		currents = problem.initial_states[:k]
		for each iteration:
			for state in currents:
				if state is currents:
					if state is goal:
						return state
			all_successors = []
			for state in currents:
				for each successor of state:
					all_successors.append(successor)
			all_successors.sort(key=some function)
			
			currents = all_successors[:k]
```

## Evolutionary (Genetic) Algorithms
- Inspired by microbiology
	- state represented as a chromosome expressing genes
	- each individual has a fitness level
	- reproduction involves recombination (crossover): taking one part from one parent and another part from the other parent
	- random mutations damage DNA
```Python
	def genetic_algorithm(problem, pop_size):  
		current_population = initialize_population(pop_size)  
		for generation in range(1, ...):  
			fitness = calculate_fitness(current_population)  
			population = []  
			for i in range(pop_size):  
				parent1, parent2 = select_parents(fitness)  
				child = reproduce(parent1, parent2)  
				if small random probability:  
					child = mutate(child)  
				population.append(child)  
			current_population = population  
		return individual with the best fitness
```

## Gradient Descent
- For continuous search spaces
- If we have a function $f(x)$ that tells us the value of each state $x$
	- we can compute the gradient (derivative)
	- take a step in that direction
		- $x = x - n \frac{d}{dx} f(x)$

## Summary
- Algorithms for optimizing functions
	- Hill climbing
	- Simulated annealing
	- Genetic algorithms