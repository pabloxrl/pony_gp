`pony_gp` is an implementation of Genetic Programming(GP), see e.g. 
<http://geneticprogramming.com>. The purpose of `pony_gp` is to describe how 
the GP algorithm works. The intended use is for teaching. The aim is to allow
the developer to quickly start using and developing. The design is supposed 
to be simple, self contained and use core python libraries. 

# Run

Find a equation for the input given an output.

```python
python pony_gp.py
```

The input with their respective output is in the file `fitness_case.csv`. The 
exemplars are generated from `y = x0^2 + x1^2` from range `[-5,5]`

## Requirements

Python 3

## Usage

```
Usage: pony_gp.py [options]

Arguments:
  -h, --help            show this help message and exit
  -p POPULATION_SIZE, --population_size=POPULATION_SIZE
                        Population size is the number of individual solutions
  -m MAX_DEPTH, --max_depth=MAX_DEPTH
                        Max depth of tree. Partly determines the search space
                        of the solutions
  -e ELITE_SIZE, --elite_size=ELITE_SIZE
                        Elite size is the number of best individual solutions
                        that are preserved between generations
  -g GENERATIONS, --generations=GENERATIONS
                        Number of generations. The number of iterations of the
                        search loop.
  --ts=TOURNAMENT_SIZE, --tournament_size=TOURNAMENT_SIZE
                        Tournament size. The number of individual solutions
                        that are compared when determining which solutions are
                        inserted into the next generation(iteration) of the
                        search loop
  -s SEED, --seed=SEED  Random seed. For replication of runs of the EA. The
                        search is stochastic and and replication of the
                        results are guaranteed the random seed
  --cp=CROSSOVER_PROBABILITY, --crossover_probability=CROSSOVER_PROBABILITY
                        Crossover probability, [0.0,1.0]. The probability of
                        two individual solutions to be varied by the crossover
                        operator
  --mp=MUTATION_PROBABILITY, --mutation_probability=MUTATION_PROBABILITY
                        Mutation probability, [0.0, 1.0]. The probability of
                        an individual solutions to be varied by the mutation
                        operator
  --fc=FITNESS_CASES, --fitness_cases=FITNESS_CASES
                        Fitness cases filename. The exemplars of input and the
                        corresponding out put used to train and test
                        individual solutions
  --tts=TEST_TRAIN_SPLIT, --test_train_split=TEST_TRAIN_SPLIT
                        Test-train data split, [0.0,1.0]. The ratio of fitness
                        cases used for trainging individual solutions
```             

## Output
Keep running until fitness for train data and test data reaches approximately 0.
```
#Statistics on Data
Reading: csv file containing input and output data for program to execute 
         headers: [input(s), output] exemplars: amount of input and output points   

#Refer to the above usage section to apprehend this line
#Individual Statistics
Initial individual nr:individual number nodes: amount of nodes or different symbols in the individual
max_depth: max depth of individual(refer to usage): individual generated

#Generation Statistics
Generation:generation number fit_ave:average fitness of the generation 
           size_ave:average number of nodes in the genearation amongst all data points 
           depth_ave:average max_tree depth max_size: maximum number of nodes 
           max_depth: maximum depth max_fit: maximum fitness 
           best_solution:{'genome': individual formula/tree, 'fitness': fitness of genome}

#Best Solution Statistics
Best solution on train data:{'genome': individual formula/tree, 'fitness': fitness of genome}
Best solution on test data:{'genome':individual formula/tree, 'fitness':fitness of genome}

``` 
Example:
``` 
Reading: fitness_cases.csv headers: ['x0', 'y'] exemplars:19
Initial tree nr:0 nodes:1 max_depth:0: ['x0']
Initial tree nr:1 nodes:1 max_depth:0: ['1']
Initial tree nr:2 nodes:7 max_depth:2: ['+', ['*', ['1'], ['x0']], ['+', ['1'], ['0']]]
Initial tree nr:3 nodes:1 max_depth:0: ['0']
Generation:0 fit_ave:-8.65+-8.647 size_ave:2.50+-2.598 depth_ave:0.50+-0.866 max_size:7 max_depth:2 max_fit:-0.000000 best_solution:{'genome': ['x0'], 'fitness': -1.0}
Generation:1 fit_ave:-0.25+-0.433 size_ave:7.00+-0.000 depth_ave:2.00+-0.000 max_size:7 max_depth:2 max_fit:-0.000000 best_solution:{'genome': ['+', ['*', ['1'], ['x0']], ['+', ['1'], ['0']]], 'fitness': -0.0}
Best solution on train data:{'genome': ['+', ['*', ['1'], ['x0']], ['+', ['1'], ['0']]], 'fitness': -0.0}
Best solution on test data:{'genome': ['+', ['*', ['1'], ['x0']], ['+', ['1'], ['0']]], 'fitness': -0.0}
``` 

