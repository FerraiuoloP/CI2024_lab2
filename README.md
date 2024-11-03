# Travelling Salesman Problem

Solve the given TSP instances using both a fast but approximate algorithm and a slower, yet more accurate one. Report the final cost and the number of steps.  
Instances can be found at [this link](https://github.com/squillero/computational-intelligence/tree/master/2024-25/cities).

## Fast but approximate algorithm : Greedy Algorithm
Simple greedy algorithm for a fast solution to the TSP problem. The algorithm starts from a random city and then moves to the nearest city. Repeats until all cities are visited.
### Performance table
**Note**: by steps we mean the number of iterations of the algorithm. The number of steps is not the same as the number of cities in the dataset.
| Dataset | Steps | Min path length |
| --- | --- | --- |
|Vanuatu | 8 | 1475.528 Km |
| Italy | 46 | 4436.031 Km |
| Russia | 167 | 42334.164 Km |
| US | 340 | 48050.025 Km  |
| China | 746 | 63962.918 Km |

## Slow but accurate algorithm : Genetic Algorithm
It is a genetic algorithm implemented in the following way:
1. **Initialization**: the population is initialized with a random permutation of the cities + the best solution found so far with the greedy algorithm.
2. **Parent selection**: a Rank-based selection is used to select the parents (half of the population).
3. **Genetic operators**: probabilistic choice of the genetic operators (from Hyper-Modern GA).
    - **Crossover**: a 2 point crossover is used to generate the offspring.
    - **Mutation**: an Inversion Mutation is used to mutate the offspring.
4. **Population management**: offspring are added to the parents (mu+lambda management) to create a new population.
5. **Parent selection**: Deterministic selection of the best `POPULATION_SIZE` individuals to form the next generation.

### Performance table
**Note**: by `Steps` we mean the number of iterations of the algorithm while by `Fitness calls` we mean the number of times the fitness function is called. The `Best sol iter` is the iteration number in which the best solution has been found (out of `Steps` iterations).\
I adjuststed the number of steps based on the dataset.

| Dataset | Steps | Fitness calls | Best sol iter | Best sol length |
| --- | --- | --- | --- | --- |
|Vanuatu | 100 | 10052 | 21 | 1345.544 Km |
| Italy | 1000 | 55052 | 566 | 4181.619 Km |
| Russia | 10000 | 505052 | 9807 | 33975.162 Km |
| Russia | 30000 | 1505052 | 28079 | 33528.567 Km |
| US | 10000 | 505052 | 9923 | 41695.848 Km | 
| US | 30000 | 1505052 | 29145 | 41213.701 Km |
| China | 10000 | 505052 | 9847 | 59648.475 Km |
| China | 30000 | 1505052 | 29922 | 56652.405 Km |


*We can notice that increasing the number of steps in the last datasets a better a slightly better solution is found*

# How to run
Create a `cities` folder at the same level of the ipynb file and put the datasets (found [here](https://github.com/squillero/computational-intelligence/tree/master/2024-25/cities)) inside it.  
Then, to run in a virtual environment follow the istructions [here](https://github.com/squillero/computational-intelligence/tree/master/2024-25/contrib/poetry_installation_guide) (skipping the creation of .toml and .ipynb files)



## Contributors
Some techniques implemented in my proposal were discussed and developed jointly with my colleague [GDennis01](https://github.com/GDennis01/). In particoular we started from the same template, then we devised together a way to implement a crossover/mutation. We concluded together that the Inversion Mutation operator was the best choice for our scenario.
