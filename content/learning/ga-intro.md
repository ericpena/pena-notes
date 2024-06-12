---
title: "First Genetic Algorithm"
author: "Eric Peña"
date: 2020-04-14T00:00:00-00:00
description: "Logistic Map"
type: non-technical_note
draft: false
---

# What is a Genetic Algorithm
Evolutionary programming is a family of global optimization techniques that are biologically inspired. It works similarly to the natural process in evolutionary biology. Trial and error is a large component along with stochasticity and survival of the fittest. The type of evolutionary computation that we will focus on is genetic algorithms which became popular by the American Professor of Psychology, Electrical Engineering, and Computer Science, John Holland. Genetic algorithms work using natural selection of different possible solutions competing with one another. It incorporates biological concepts such as selection, crossover, and mutation. Candidate solutions can mate with each other and create offspring who can then compete with other solutions in their generation.

# Components of a Genetic Algorithm
* Gene
* Chromosome
* Population
* Fitness Function
* Selection
* Crossover
* Mutation

# Programming Genetic Algorithms in Python
It's typical to use object oriented programming when developing Genetic Algorithms in code. In our simple example, let's create a class called `Agent`. In the language of GA, these are called the *chromosome*. This chromosome will simply be a string in our program but I'd recommend always thinking in terms of GA and the termology used in this domain. If the text string represents a chromosome, then the characters that make up this string are its *genes*. Below is an example of a simple genetic algorithm that will be given the task of finding the string: `ericpena`. The algorithm is broken up into distrinct methods for clarity.


```python
from fuzzywuzzy import fuzz
import random
import string

class Agent:

	def __init__(self, length):

		# Initialize a new agent
		self.string = ''.join(random.choice(string.ascii_letters) for _ in range(length))
		self.fitness = -1

	def __str__(self):

		return 'String: ' + str(self.string) + ' Fitness: ' + str(self.fitness)
```

# Initialize Population


```python
in_str = None
in_str_len = None
population = 20
generations = 2500

def init_agents(population, length):

	return [Agent(length) for _ in range(population)]
```

# Define Fitness Function


```python
def fitness(agents):

	for agent in agents:

		agent.fitness = fuzz.ratio(agent.string, in_str)

	return agents
```

# Define Selection Criteria


```python
def selection(agents):

	agents = sorted(agents, key=lambda agent: agent.fitness, reverse=True)
	print('\n'.join(map(str, agents)))
	agents = agents[:int(0.2 * len(agents))]

	return agents
```

# Define Crossover Mechanism


```python
def crossover(agents):

	offspring = []

	for _ in range(int((population - len(agents)) / 2)):

		parent1 = random.choice(agents)
		parent2 = random.choice(agents)
		child1 = Agent(in_str_len)
		child2 = Agent(in_str_len)
		split = random.randint(0, in_str_len)
		child1.string = parent1.string[0:split] + parent2.string[split:in_str_len]
		child2.string = parent2.string[0:split] + parent1.string[split:in_str_len]

		offspring.append(child1)
		offspring.append(child2)

	agents.extend(offspring)

	return agents
```

# Define GA Mutation


```python
def mutation(agents):

	for agent in agents:

		for idx, param in enumerate(agent.string):

			if random.uniform(0.0, 1.0) <= 0.1:

				agent.string = agent.string[0:idx] + \
					random.choice(string.ascii_letters) + \
					agent.string[idx + 1:in_str_len]

	return agents
```

# Running GA


```python
def ga():
	
	agents = init_agents(population, in_str_len)

	for generation in range(generations):

		print('Generation: ' + str(generation))

		agents = fitness(agents)
		agents = selection(agents)
		agents = crossover(agents)
		agents = mutation(agents)

		if any(agent.fitness >= 90 for agent in agents):

			print('Threshold met!')
			exit(0)
```


```python
if __name__ == '__main__':
	
	in_str = 'ericpena'
	in_str_len = len(in_str)
	ga()
```

# Results
* Generation 0 — String: CKvOGQJL Fitness: 0
* Generation 3 — String: iJdvcmeX Fitness: 38
* Generation 11 — String: iJOqcmea Fitness: 50
* Generation 85 — String: evXicpea Fitness: 75
* Generation 299 — String: esricena Fitness: 88

As can be seen, the longer we allow this Genetic Algorithm to run, the closer the solution gets to the *objective string*: `ericpena`
