The overall structure of the evolutionary algorithm is solid. The core building blocks like selection, crossover, mutation and even elitism are used properly and the design follows the constraints of a TSP solver based on permutations
### Initialization
Starting from random permutations can be a good choice because it keeps the first generation diverse and helps to avoid early convergence
### Selection
Tournament selection is well implemented, it applies steady selection pressure and is easy to tune.
A nice improvement is to make the tournament size change dynamically during the run (for example a deterministic approach moving between 2 and 5, but adaptive or self-adaptive strategies are also possible). This gives more exploration early on and gradually shifts toward exploitation as the search continues
### Crossover
Both PMX and Inver over are well implemented and produce valid tours. Their combination in the code gives a mix of structure inheritance and randomness that helps to maintain variety 
### Mutation
The basic swap mutation is correct and keeps tours valid.
Maybe it’s also a good idea to try something else, like a reverse/inversion mutation. Inversion is good because reversing a path segment might remove bad edges and shorten the tour. It works best for symmetric TSP, where edge direction doesn’t matter
### Elitism
Elitism is applied properly and ensures that strong solutions are not lost while still allowing the rest of the population to evolve freely
### Stopping conditions
the algorithm could still benefit from an optional early-stoppage based on lack of improvement, but this doesn’t affect correctness, just the execution time
### Fitness evaluation
Using the network library worked fine but maybe switching to matrix-based evaluation would speed things up. Also this is not required for correctness but might be helpful for large instances
### Handling parameters
The parameters are clear and easy to adjust. But as said above, having dynamic parameters in the code is a good idea and might bring some significant improvements

### Result
With two small adjustments (a dynamic tournament size (2–5) and trying with an inversion mutation) the performance on the g_50 instance improved from 2874 down to 2547

