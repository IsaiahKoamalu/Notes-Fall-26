## Particle Swarm Optimization
- Particles start with an initial position and velocity
- Particle tries to move in the direction of:
	- the best it has seen so far (cognitive)
	- the global best so far (social)
```Python
	@dataclass
	class Particle:
		position: tuple
		velocity: tuple
		best_position: tuple
		best_score: float

	def pso():  
		particles = [...] # initialize particles randomly  
		global_best_score = inf  
		global_best_position = None  
		c1 = ... # weight for cognitive  
		c2 = ... # weight for social  
		w = ... # weight for inertia (previous velocity)  
		for each iteration:  
			for each particle:  
			# move particle  
			r1 = random()  
			r2 = random()  
			cognitive_component = r1 * (particle.best_position - particle.position)  
			social_component = r2 * (global_best_position - particle.position)  
			particle.velocity = w * particle.velocity + c1 * cognitive_component + c2 *  
			social_component  
			particle_position += particle.velocity  
			# evaluate fitness and update best  
			score = value(particle.position)  
			if score < particle.best_score:  
				particle.best_score = score  
				partice.best_position = particle.position  
				if score < global_best_score:  
					global_best_score = score  
					global_best_position = particle.position
```

- Parameter tuning
	- inertia < 1
	- c1 and c2 usually [1, 3]
- Benefits
	- gradient free
	- no assumptions about the problem
	- fast convergence
- Drawbacks
	- not guaranteed to find the optimal solution
	- sensitive to parameter choices

## Linear Programming
- Linear optimization: optimize a linear objective function with the linear equality and linear inequality constraints.
**Example:** Wheat makes $5 per bushel, requires 1 fertilizer and 2 pesticide. Corn makes $4 per bushel, requires 2 fertilizer and 1.5 pesticide. Maximize profits, subject to the constraints.
     Available land: $w+c <= 100$
	 Available fertilizer: $1w + 2c <= 50$
	 Available pesticide: $1.5w + 1c <= 50$
```Python
# x1 = wheat - $5 profit, requires 1 fertilizer, 2 pesticide  
# x2 = corn - $4 profit, requires 1.5 fertilizer, 1 pesticide  
# constraints  
# available area: x1 + x2 <= 100 acres  
# available fertilizer: 1*x1 + 2*x2 <= 50  
# available pesticide: 1.5*x1 + 1*x2 <= 50  
# linprog performs minimization, so negate the coefficients  
c = [-5, -4]  
# Budget constraint: 15*x1 + 3*x2 <= 100  
A_ub = [[1, 1], [1, 2], [1.5, 1]]  
b_ub = [100, 50, 50]  
# Nonnegative quantities  
bounds = [  
	(0, None), # 0 < x1 < inf  
	(0, None), # 0 < x2 < inf  
]  
result = linprog(  
	c=c,  
	A_ub=A_ub,  
	b_ub=b_ub,  
	bounds=bounds,  
	# integrality=True, # if values must be integers  
	method="highs",  
)  
print(result)  
print("Wheat:", result.x[0])  
print("Corn:", result.x[1])  
print("Profit:", -result.fun
```

## Integer Linear Programming
- `scipy.optimize.milp`
	- values can be integers (integrality)
	- more flexible API
```Python
# Maximize 5*x1 + 4*x2.  
# scipy.optimize.milp minimizes, so negate the objective.  
c = np.array([-5, -4])  
# Constraint matrix:  
# 0 <= x1 + x2 <= 100 area  
# 0 <= x1 + 2*x2 <= 50 fertilizer  
# 0 <= 1.5*x1 + x2 <= 50 pesticide  
A = np.array([  
	[1, 1],  
	[1, 2],  
	[1.5, 1],  
])  
constraints = LinearConstraint(  
	A,  
	lb=[0, 0, 0],  
	ub=[100, 50, 50],  
)  
# x1, x2 >= 0  
bounds = Bounds(  
	lb=[0, 0],  
	ub=[np.inf, np.inf],  
)  
# Require both crop-acreage variables to be integers  
integrality = [1, 1] # 0 = continuous, 1 = integer  
result = milp(  
	c=c,  
	integrality=integrality,  
	bounds=bounds,  
	constraints=constraints,
)
```

