---
title: "Different Kind of Birthday Puzzle"
author: "Eric Peña"
date: 2022-04-24T00:00:00-07:00
description: "Cellular Automata Introduction"
type: non-technical_note
draft: true
---

------------------------------------------------------

# Motivation

> "There's like 200 poe" -- John von Neumann

I was watching Seinfeld and Elaine...

# Canonical Birthday Problem

The canonical birthday problem looks at a different probability...you can ask two different questions...prob give n peopel or how many people to get reach 50%
but this new probability question isn't as straight forward.

# The Answer - In Depth

Let's begin to think about the ploblem at hand...it never actually reaches one and is exactly zero if n < 365 given this is not a leap year and birthdays are uniformly distributed



Cellular automata (CA) have the ability to generate complex global patterns from simple local rules. Cellular automata are discrete dynamical systems used primarily as a computational model to study how spatiotemporal patterns evolve in a wide range of phenomena. This idea was first developed by Stanisław Ulam and John von Neumann in the 1940s. It has since been applied to an array of disparate fields: computer science, mathematics, climate science, complexity science, art, music, and many others.
    
The model is quite simple and easy for anyone to understand. It consists of a regular finite or infinite grid of cells where each cell can exist in a particular state. For instance, the states for a two-state CA can be: \{*dead*,*alive*\}, \{0,1\}, \{*off*,*on*\}, *etc*. --- whichever naming convention is most relevant to the application. The set of neighboring cells that surround a center cell is called a *neighborhood*. Two neighborhood structures that are key to this thesis exist on two-dimensional spatial grids: the Moore and von Neumann neighborhoods. The *Moore* neighborhood consists of eight neighboring cells of the center cell as seen in Figure **1**. The *von Neumann* neighborhood consists of the cells that are north, south, east, and west of the center cell as seen in Figure **2**. To provide a sense of scale, for a two-dimensional system with a Moore neighborhood, there exists $2^{2^9}$ or $1.34 \times 10^{154}$ possible cellular automata rules.


![Figure 1 - Moore Neighborhood](cellular_automata_intro/moore.png)
Figure **1** above shows the Moore Neighborhood.
![Figure 2 - Moore Neighborhood](cellular_automata_intro/vonneumann.png)
Figure **2** above shows the von Neumann Neighborhood.
    
### Layman's Terms.
A simple analogy may aid the reader in understanding the cellular automata setup. Let us begin by thinking about a two dimensional grid of cells that are all identical. This is akin to a simple universe whose occupants are people who are all similar and only capable of performing the same two tasks: to become alive or die---those who are alive may die and those who are dead may resurrect! The task they perform depends on the number of people around them who are alive and dead in one time instance. This is determined by clear, unambiguous rules or laws. For example, a simple and completely made-up rule could be stated as: "If you are alive *and* four or more of your neighbors are alive, then you will die in the next time step". Every person in this universe obeys the same universal laws---these laws are the *physics* that governs this universe. Given these laws (i.e., cellular automata rules) and a starting population of living and dead occupants (i.e., initial states), we can compute the state of future occupants---this will tell us who is alive and who is dead, after applying the rules onto this universe some predefined number of times.

---------------------------------------
### Rule 90

```python
RulePlot[CellularAutomaton[90]]
```

![Figure 4 - Rule30](cellular_automata_intro/rule90-ruleplot.png)

```python
ArrayPlot[CellularAutomaton[90, {{1}, 0}, {200, 200}], Frame -> False]
```

## References
* `Stephen Wolfram. \Statistical mechanics of cellular automata". In: Reviews of modern physics 55.3 (1983), p. 601.`
* `Norman H Packard and Stephen Wolfram. \Two-dimensional cellular automata". In: Journal of Statistical physics 38.5 (1985), pp. 901{946.`
* `Stephen Wolfram. A new kind of science. Vol. 5. Wolfram media Champaign, IL, 2002.`
* `Nino Boccara. Modeling complex systems. Springer Science & Business Media, 2010.`
* `Hiroki Sayama. Introduction to the modeling and analysis of complex systems. Open SUNY Textbooks, 2015.`
* `Yaneer Bar-Yam. Dynamics of complex systems. CRC Press, 2019.`

