---
title: "Diversity in Competitive Threshold Linear Networks"
author: "Eric Peña"
date: 2019-12-11T00:00:00-07:00
description: "Diversity in Competitive Threshold Linear Networks"
type: non-technical_note
draft: false
---
<!-- ![](img_ctln/featured.png) -->

---------------------------------------

![](img_ctln/network.png)
Figure 1 — Directed Network Which Represents Threshold Linear Network

#### Adjacency Matrix Representing Directed Network

$$\begin{pmatrix} 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 \\\ 1 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0\end{pmatrix}$$

<div>$$\frac{d x_i}{dt} = -x_i + \left[ \sum_{j=1}^{n} W_{ij} x_j + \theta \right]_+ i = 1, \ldots, n$$</div>

![](img_ctln/plot.png)
Figure 2 — Solution Via Numerically Solving Differential Equation

## Initial Conditions
The initial conditions applied to the network above are the following:

* $x1[0] = .9$
* $x2[0] = x3[0] = x4[0] = x5[0] = x6[0] = x7[0] = x8[0] = x9[0] = x10[0] = .5$

![](img_ctln/ctln.gif)
Figure 3 — Dynamics of Directed Network Which Represents Competitive Threshold Linear Network

<p><iframe src="https://docs.google.com/presentation/d/1fx30MNJ0vK8NCKlWVHHwYNCAWU1UkN1zVmRUMJ6gjVQ/edit?usp=sharing" frameborder="0" width="800" height="600" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe></p>





