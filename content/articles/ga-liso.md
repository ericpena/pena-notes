---
title: "Genetic Algorithm — Cellular Automata Optimization"
author: "Eric Peña"
date: 2019-12-01T00:00:00-07:00
description: "Genetic Algorithm — Cellular Automata Optimization"
type: non-technical_note
draft: false
---

# Abstract

The mechanism by which nature exhibits emergent patterns and behaviors has been a mystery throughout history. One application that has been developed which tends to mimic nature is Conway’s Game of Life — an application in the field of cellular automata. The ability to predict a final state of a system, given an initial state in the context of Game of Life, come as an insurmountable task. In this work, genetic algorithms are explored along with how they may be used to search for initial conditions such that their final outcomes are optimal. Optimal final states may be defined in terms of growth, diversity, and density of the cellular automaton evolution. This may be beneficial in exploring the way in which coupled components interact in mathematical and physical systems.

# Motivation

Many will claim that the ultimate objective of science is to understand and model the natural world. There are many phenomena in nature whose patterns and behavior seem somewhat unpredictable yet these resulting patterns appear highly structured and organized. Scientists and mathematicians have developed techniques such as chaos theory and cellular automata for the attempt to model nature in its truest sense. In this paper we will take an approach to understand how structure stems from randomness in a cellular automata model. A cellular automaton is defined in terms of clear rules on each individual cell and its well defined neighborhood of cells that surround it. We will go into detail as to what this means in later chapters but let us begin by thinking about a two dimensional grid of cells that are all identical. We can even analogize this to a simple universe of people who are all the same and only know how to do the same task: become alive or die. Whether they become alive or die depends on the number of people around them who are either alive or dead given clear, unambiguous rules. Every person in this universe obeys the same universal laws—namely, in this context, the cellular automata rules. Given a clear and finite set of cellular automata rules and given a defined initial state, we can compute the state of a future grid—this will tell us which cells are alive and which are dead, after applying the rules onto the grid some predefined number n times. The defined cellular automata rules used in this report are those defined by Conway’s Game of Life. The well defined rules for Conway’s Game of Life will be explained in section 2.2.

![](img_liso/dna.png)

# Thesis Objective

The objective of this project is to understand which initial conditions (initial states), given a set of welldefined cellular automata rules, produce the most optimized final states after n iterations of applying these rules. The variable being optimized is the fitness value where fitness is defined in terms of what I call growth, diversity, and density of the final state grids. These three terms and how they relate to this specific application are further explained in section 4.4. To make the objective clear, I will state it here and repeat it throughout the report to make sure we are on track with achieving it.

>OBJECTIVE: Given well-defined cellular automata rules defined by Conway’s Game of Life, determine an initial state that produces an optimal final state in terms of growth, diversity, and density after a finite number of iterations.

# Thesis Outline

The report is organized in chapters that describe the major components of this project. The topics covered are the background of the application (Chapter 2), an overview of the genetic algorithms and how they are used to optimize initial states (Chapter 3), the details of the genetic algorithm implementation (Chapter 4), a description of the results (Chapter 5), and a few concluding thoughts and considerations for improvements and future work (Chapter 6).

# The Report
[![Foo](img_liso/pdf.png)](img_liso/LISO_Project.pdf)