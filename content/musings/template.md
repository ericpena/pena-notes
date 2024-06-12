---
title: "Template"
author: "Eric Peña"
date: 2021-12-09T00:00:00-07:00
description: "Template"
type: non-technical_note
draft: true
---

# Introduction

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Lacus vestibulum sed arcu non. Odio pellentesque diam volutpat commodo sed egestas. Nibh nisl condimentum id venenatis. Ut eu sem integer vitae justo eget magna. Orci a scelerisque purus semper eget duis at tellus at. Etiam dignissim diam quis enim lobortis scelerisque fermentum dui faucibus. Feugiat scelerisque varius morbi enim nunc faucibus. Et odio pellentesque diam volutpat commodo sed egestas egestas. Enim ut tellus elementum sagittis vitae et leo duis.

Ultricies leo integer malesuada nunc vel. Duis convallis convallis tellus id interdum velit laoreet. Aliquet porttitor lacus luctus accumsan tortor posuere ac ut consequat. Montes nascetur ridiculus mus mauris. Mauris nunc congue nisi vitae suscipit tellus mauris a. Consequat id porta nibh venenatis cras sed. Consequat mauris nunc congue nisi. Turpis massa tincidunt dui ut ornare lectus sit. Mauris in aliquam sem fringilla ut morbi tincidunt augue. Libero enim sed faucibus turpis in eu. Sed id semper risus in hendrerit gravida. Tortor dignissim convallis aenean et tortor at risus viverra. In cursus turpis massa tincidunt dui ut ornare lectus. Lectus nulla at volutpat diam ut venenatis. Euismod elementum nisi quis eleifend. Eget dolor morbi non arcu. Bibendum at varius vel pharetra vel turpis nunc eget lorem. Nulla at volutpat diam ut venenatis tellus. Volutpat maecenas volutpat blandit aliquam.

-------------------------

# Header

### Header 3
$$P_{i\text{ = }0} = 1$$
$$P_{i\text{ = }1} = \frac{2\cdot n - 2\cdot i}{2\cdot n - i} = \frac{2\cdot 3 - 2\cdot 1}{2\cdot 3 - 1} = \frac{4}{5}$$
* So for the third sock $(i = 2)$, we ask what is the probability of choosing a sock given that it doesn't match what you already have:
$$P_{i\text{ = }2} = \frac{2\cdot n - 2\cdot i}{2\cdot n - i} = \frac{2\cdot 3 - 2\cdot 2}{2\cdot 3 - 2} = \frac{1}{2}$$
* Finally, to end this "three socks/three pairs" example, we'll just multiply all these individual probabilities together to get a final probability! The probability of choosing three socks from three pairs such that none of them match is:
$$P_{i\text{ = }0} \cdot P_{i\text{ = }1} \cdot P_{i\text{ = }2} = 1 \cdot \frac{4}{5} \cdot \frac{1}{2} = 0.40 = 40\\%$$

### Header 3
* Let's generalize this solution by saying that we have $n$ pairs of socks in a basket and we're choosing $k$ individual socks one by one. The probability that all $k$ of the chosen socks are unique is:
$$P = \prod^{k - 1 \le n - 1}_{i\text{ = }0}\frac{2\cdot n - 2\cdot i}{2\cdot n - i}$$


```python
from functools import reduce

probabilities = [reduce((lambda x, y: x * y), [(2*n - 2*i) / (2*n - i) for i in range(n)]) for n in range(1,11)]
list(zip([n for n in range(1, 11)], probabilities))
```




    [(1, 1.0),
     (2, 0.6666666666666666),
     (3, 0.4),
     (4, 0.22857142857142856),
     (5, 0.12698412698412698),
     (6, 0.06926406926406926),
     (7, 0.037296037296037296),
     (8, 0.01989121989121989),
     (9, 0.010530645824763473),
     (10, 0.0055424451709281414)]



# Choosing Socks Simultaneously

* To begin, let's start with the later. The number of ways that $k$ socks can be chosen from $n$ pairs (regardless of socks matching or not) is $2n \choose k$:
$${2n \choose k} = \frac{(2n)!}{k! (2n - k)!}$$
* On the other hand, the number of ways that we can choose $k$ ***unique*** socks from $n$ pairs is:
$${n \choose k}{2 \choose 1}^k$$
* The ${n \choose k}$ term is the act of choosing $k$ pairs and the ${2 \choose 1}^k$ term is the act of choosing 1 sock (out of two) from each of those $k$ pairs.
* To put it all together, the final probability expression that we're after is:
$$P = \frac{{n \choose k}{2 \choose 1}^k}{2n \choose k}$$
* Let's show that this is indeed the same thing in Mathematica!

![png](unmatching-socks/nk_arrayplot.png)
