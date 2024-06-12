---
title: "Data Types in R"
Description: "Important Data Types For R Programming"
date: 2020-05-21T00:00:00-00:00
draft: false
author: "Eric Peña"
type: non-technical_note
---

# "Truth is ever to be found in simplicity, and not in the multiplicity and confusion of things."---Isaac Newton

I approached R in the same way I would any language. I immediately delve into for-loops, conditional statements, user-defined functions, classes, and so on. I didn't pay much attention to data types at first - assuming they're not much different than what I've seen already. I found myself using dataframes and matricies often with low confidence and a lingering confusion. I needed to know how these R data structures were related. I finally created these notes for myself to get a grip on the topic. Hopefully you find value in them as well.

The data structures we will cover:

* **[Vectors](#vector)**
* **[Matrices](#matrix)**
* **[Arrays](#array)**
* **[Lists](#list)**
* **[Data Frames](#dataframe)**
* **[Factors](#factor)**
* **[Tables](#table)**

For each data type, we will review the basics of:

* **Creation**
* **Adding Element**
* **Deleting Elements**
* **Indexing**
* **Filtering**
* **and More**

---

# Vector
<!---------------------------------------------------------->
<!---------------------------------------------------------->

### <span style="color:#E74C3C">Introduction</span>

All elements in an R vector must have the same mode: *integer*, *numeric*, *character*, *logical*, *complex*, etc.

### <span style="color:#E74C3C">Creation</span>

``` r
x <- c(88, 12, 23, 74)
x
```
``` r
    ## [1] 88 12 23 74
```
### <span style="color:#E74C3C">Adding Element</span>

Adding -44 to vector `x`:

``` r
x <- c(x,-44)
x
```
``` r
    ## [1]  88  12  23  74 -44
```
or:

``` r
x[5] <- -44
x
```
``` r
    ## [1]  88  12  23  74 -44
```
### <span style="color:#E74C3C">Remove Element</span>

Remove 23 from `x`:

``` r
x <- x[-3]
x
```
``` r
    ## [1]  88  12  74 -44
```
It's possible to remove several items at once:

``` r
x <- x[-3:-5]
x
```
``` r
    ## [1] 88 12
```
### <span style="color:#E74C3C">Indexing</span>

``` r
x <- rep(1,10)
x[4] <- 3
x
```
``` r
    ##  [1] 1 1 1 3 1 1 1 1 1 1
```
``` r
x[4]
```
``` r
    ## [1] 3
```
### <span style="color:#E74C3C">Filtering</span>

``` r
x[6] <- 5
x[9] <- 2
x[x > 2]
```
``` r
    ## [1] 3 5
```
### <span style="color:#E74C3C">Combining Vectors</span>

Find the length of a vector with `length(x)`:

When adding two vectors, the lengths of the vectors must be the same or one must be a multiple length of the other. When a vector isn't long enough to add to another vectors, it will keep repeating itself however many times it needs in order for the lengths to match.

``` r
y <- x + x; y
```
``` r
    ##  [1]  2  2  2  6  2 10  2  2  4  2
```
``` r
z <- x + c(1,2,3,4,5); z
```
``` r
    ##  [1] 2 3 4 7 6 6 3 4 6 6
```
``` r
error <- x + c(1,2,3,4); error
```
``` r
    ## Warning in x + c(1, 2, 3, 4): longer object length is not a multiple of
    ## shorter object length

    ##  [1] 2 3 4 7 2 7 4 5 3 3
```

---

# Matrix
<!---------------------------------------------------------->
<!---------------------------------------------------------->

### <span style="color:#E74C3C">Introduction</span>

A matrix is essentially a vector with two attributes. All the columns in a matrix must have the same mode: *integer*, *numeric*, *character*, *logical*, *complex*, etc. in the same way it does for a vector. Matricies are special cases of a more general R type of object: *arrays* - which we will read about next. Arrays can be multidimensional. 

### <span style="color:#E74C3C">Creation</span>

One way to create a matrix:

``` r
y <- matrix(c(1,2,3,4), nrow = 2, ncol = 2)
```

or simply:

``` r
y <- matrix(c(1,2,3,4), nrow = 2)
y
```
``` r
    ##      [,1] [,2]
    ## [1,]    1    3
    ## [2,]    2    4
```
Using the `byrow` argument (default = FALSE):

``` r
m <- matrix(c(1,2,3,4,5,6), nrow = 2, byrow = T)
m
```
``` r
    ##      [,1] [,2] [,3]
    ## [1,]    1    2    3
    ## [2,]    4    5    6
```
### <span style="color:#E74C3C">Adding and Removing Rows and Columns</span>

Rows and columns may be added and deleting from a matrix with operations analogous to the vector operations of adding and deleting. These functions are `rbind` and `cbind`.

Adding a column:

``` r
ones_column <- matrix(rep(1,2)); ones_column; m
```
``` r
    ##      [,1]
    ## [1,]    1
    ## [2,]    1

    ##      [,1] [,2] [,3]
    ## [1,]    1    2    3
    ## [2,]    4    5    6
```
``` r
cbind(m, ones_column)
```
``` r
    ##      [,1] [,2] [,3] [,4]
    ## [1,]    1    2    3    1
    ## [2,]    4    5    6    1
```
Adding a row: (don't forgot to adjust the row number: `nrow = 1`)

``` r
ones_row <- matrix(rep(1,3), nrow = 1); ones_row; m
```
``` r
    ##      [,1] [,2] [,3]
    ## [1,]    1    1    1

    ##      [,1] [,2] [,3]
    ## [1,]    1    2    3
    ## [2,]    4    5    6
```
``` r
rbind(ones_row, m)
```
``` r
    ##      [,1] [,2] [,3]
    ## [1,]    1    1    1
    ## [2,]    1    2    3
    ## [3,]    4    5    6
```
Rows may be added by creating matricies and copying:

``` r
new_matrix <- matrix(nrow = 3, ncol = 3)

addded_row <- matrix(c(7,8,9), nrow = 1)

new_matrix[1:2,1:3] <- m
new_matrix[3,1:3] <- addded_row
new_matrix
```
``` r
    ##      [,1] [,2] [,3]
    ## [1,]    1    2    3
    ## [2,]    4    5    6
    ## [3,]    7    8    9
```
You can use `rbind` and `cbind` to reassign values. This is a form of deleting data.

``` r
m <- matrix(1:6, nrow = 3); m
```
``` r
    ##      [,1] [,2]
    ## [1,]    1    4
    ## [2,]    2    5
    ## [3,]    3    6
```
``` r
m <- m[c(1,3),]; m
```
``` r
    ##      [,1] [,2]
    ## [1,]    1    4
    ## [2,]    3    6
```
### <span style="color:#E74C3C">Indexing</span>

To retrieve information from a matrix:

``` r
m[,2]
```
``` r
    ## [1] 4 6
```
``` r
m[2,]
```
``` r
    ## [1] 3 6
```
``` r
m[2,2]
```
``` r
    ## [1] 6
```
Values may be changed in a matrix as well:

``` r
m[2,2] <- 66; m
```
``` r
    ##      [,1] [,2]
    ## [1,]    1    4
    ## [2,]    3   66
```
### <span style="color:#E74C3C">Filtering</span>

``` r
x <- matrix(c(1,2,3,2,3,4), nrow = 3, byrow = F); x
```
``` r
    ##      [,1] [,2]
    ## [1,]    1    2
    ## [2,]    2    3
    ## [3,]    3    4
```
``` r
x[x[,2] >= 3]
```
``` r
    ## [1] 2 3 3 4
```
``` r
j <- x[,2] >= 3
x[j,]
```
``` r
    ##      [,1] [,2]
    ## [1,]    2    3
    ## [2,]    3    4
```
### <span style="color:#E74C3C">Matrix Math</span>

``` r
y
```
``` r
    ##      [,1] [,2]
    ## [1,]    1    3
    ## [2,]    2    4
```
Mathematical Matrix Multiplication

``` r
y %*% y
```
``` r
    ##      [,1] [,2]
    ## [1,]    7   15
    ## [2,]   10   22
```
Mathematical Muliplication of Matrix by Scalar

``` r
3*y
```
``` r
    ##      [,1] [,2]
    ## [1,]    3    9
    ## [2,]    6   12
```
Mathematical Matrix Addition

``` r
y + y
```
``` r
    ##      [,1] [,2]
    ## [1,]    2    6
    ## [2,]    4    8
```
 
 ---

# Array
<!---------------------------------------------------------->
<!---------------------------------------------------------->

### <span style="color:#E74C3C">Introduction</span>

The mechanics of an array is very similar to that of a matrix in R. Unlike a matrix, an array can represent data in higher than two dimensions. We may build a three-dimensional array by conbining two matricies, we can build four-dimensional arrays by combining two or more three-dimensional arrays, and so on.

---

# List
<!---------------------------------------------------------->
<!---------------------------------------------------------->

### <span style="color:#E74C3C">Introduction</span>

List are unique in that not all elements have to be of the same mode. List structures can combine different types. An R list is similar to a Python dictionary or C struct. List form the foundation for data frames, object oriented programming (R classes), and more.

### <span style="color:#E74C3C">Creation</span>

If we wanted to create an employee database, we could start with:

``` r
j <- list(name = "Eric", salary = 45000, union = T)
j
```
``` r
    ## $name
    ## [1] "Eric"
    ## 
    ## $salary
    ## [1] 45000
    ## 
    ## $union
    ## [1] TRUE
```
The component names are called *tags*.

### <span style="color:#E74C3C">Adding Element</span>

New components can be added after a list is created:

``` r
z <- list(a = "abc", b = 12)
z
```
``` r
    ## $a
    ## [1] "abc"
    ## 
    ## $b
    ## [1] 12
```
``` r
z$c <- "sailing" # add a c component
z
```
``` r
    ## $a
    ## [1] "abc"
    ## 
    ## $b
    ## [1] 12
    ## 
    ## $c
    ## [1] "sailing"
```
Adding component can also be done via a vector index:

``` r
z[[4]] <- 28
z[5:7] <- c(F,T,T)
z
```
``` r
    ## $a
    ## [1] "abc"
    ## 
    ## $b
    ## [1] 12
    ## 
    ## $c
    ## [1] "sailing"
    ## 
    ## [[4]]
    ## [1] 28
    ## 
    ## [[5]]
    ## [1] FALSE
    ## 
    ## [[6]]
    ## [1] TRUE
    ## 
    ## [[7]]
    ## [1] TRUE
```
You can also concatenate lists:

``` r
cat <- c(list("Joe", 55000, T), list(5)); cat
```
``` r
    ## [[1]]
    ## [1] "Joe"
    ## 
    ## [[2]]
    ## [1] 55000
    ## 
    ## [[3]]
    ## [1] TRUE
    ## 
    ## [[4]]
    ## [1] 5
```
### <span style="color:#E74C3C">Remove Element</span>

You can delete a list component by setting it equal to `NULL`:

``` r
z$b <- NULL
z
```
``` r
    ## $a
    ## [1] "abc"
    ## 
    ## $c
    ## [1] "sailing"
    ## 
    ## [[3]]
    ## [1] 28
    ## 
    ## [[4]]
    ## [1] FALSE
    ## 
    ## [[5]]
    ## [1] TRUE
    ## 
    ## [[6]]
    ## [1] TRUE
```
### <span style="color:#E74C3C">Indexing</span>

You can access a list component in several different ways:

``` r
j$salary
```
``` r
    ## [1] 45000
```
``` r
j[["salary"]]
```
``` r
    ## [1] 45000
```
``` r
j[[2]]
```
``` r
    ## [1] 45000
```
**What's the deal with the single and double brackets?**

If single brackets are used, the result is another list - a sublist of the original.

``` r
j1 <- j[1:2]; j1
```
``` r
    ## $name
    ## [1] "Eric"
    ## 
    ## $salary
    ## [1] 45000
```
If double brackets are used, it is for referring to a single component and is return in the type of the component.

``` r
j[[2]]
```
``` r
    ## [1] 45000
```
The following returns an error since it's trying to return several components using a function that is meant to return one:

``` r
# j[[1:2]]
```

### <span style="color:#E74C3C">Filtering</span>

Accessing list components:

``` r
names(j)
```
``` r
    ## [1] "name"   "salary" "union"
```
We can also get the specific values instead:

``` r
ulj <- unlist(j); ulj
```
``` r
    ##    name  salary   union 
    ##  "Eric" "45000"  "TRUE"
```
Each values above has a name. This name may be removed with the following function:

``` r
names(ulj) <- NULL
ulj
```
``` r
    ## [1] "Eric"  "45000" "TRUE"
```
##### Using `lapply()` and `sapply()` functions

This applies a specific function on each of the compoenents of a list and returns another list:

``` r
lapply(list(1:3,25:29), median)
```
``` r
    ## [[1]]
    ## [1] 2
    ## 
    ## [[2]]
    ## [1] 27
```
`sapply()` returns a vector-valued answer:

``` r
sapply(list(1:3,25:29), median)
```
``` r
    ## [1]  2 27
```
### <span style="color:#E74C3C">Recursive Lists</span>

You can have lists within lists:

``` r
b <- list(u = 5, v = 12)
c <- list(w = 13)
a <- list(b, c)
a
```
``` r
    ## [[1]]
    ## [[1]]$u
    ## [1] 5
    ## 
    ## [[1]]$v
    ## [1] 12
    ## 
    ## 
    ## [[2]]
    ## [[2]]$w
    ## [1] 13
```
TIP: The concatenate function c() has an optional argument `recursive`, which controls whether *flattening* occurs when recursive lists are combined.

---

# Dataframe
<!---------------------------------------------------------->
<!---------------------------------------------------------->

### <span style="color:#E74C3C">Introduction</span>

Data frames are similar to a two dimensional matrix in that it contains rows and columns structure. However, data frame are heterogeneous; columns can be different modes. Technically, a data frame is a list whose components are equal-lengthed vectors as the columns of the data frame. Data frame are commonly used when doing data manipulation and other data analysis techniques in R.

### <span style="color:#E74C3C">Creation</span>

Creating a data frame from scratch:

``` r
scientists <- c("Einstein", "Newton")
born <- c(1879, 1642)

d <- data.frame(scientists, born, stringsAsFactors = FALSE)
d
```
``` r
    ##   scientists born
    ## 1   Einstein 1879
    ## 2     Newton 1642
```
If the named argument `stringsAsFactors` is not specified, then by default, `stringsAsFactors` will be TRUE.

Data frames can also be created from external files (.csv, .mtp, .xls, .spss, .txt) using: <br> 
``` txt
mydata = read.csv("mydata.csv", header = TRUE)
```
``` txt
mydata = read.mtp("mydata.mtp")  # read from .mtp file
```
``` txt
mydata = read.xls("mydata.xls")  # read from first sheet
```
``` txt
mydata = read.spss("myfile", to.data.frame=TRUE)
```
``` txt
mydata = read.table("mydata.txt")
```

and many more options.

### <span style="color:#E74C3C">Adding Element</span>

The `rbind()` and `cbind()` matrix functions also work in data frames to add new rows or columns of the same length.

Adding a new row:

``` r
d1
```
``` r
    ##   kids ages
    ## 1 jack   12
    ## 2 Jill   10
```
``` r
rbind(d1, list("laura", 19))
```
``` r
    ##    kids ages
    ## 1  jack   12
    ## 2  Jill   10
    ## 3 laura   19
```
Adding a column

### <span style="color:#E74C3C">Remove Element</span>

Data deletion in a data frame is similar to that of a vector.

``` r
d2
```
``` r
    ##    kids ages
    ## 1  jack   12
    ## 2  Jill   10
    ## 3 laura   19
```
``` r
d2 <- d2[-2,]
d2
```
``` r
    ##    kids ages
    ## 1  jack   12
    ## 3 laura   19
```
### <span style="color:#E74C3C">Indexing</span>

``` r
d[[1]]
```
``` r
    ## [1] "Einstein" "Newton"
```
``` r
d$scientists
```
``` r
    ## [1] "Einstein" "Newton"
```
We may also access elements in a matrix-like way we well:

``` r
d[,1]
```
``` r
    ## [1] "Einstein" "Newton"
```
It can be helpful to know the structure of the data frame and is easy to achieve:

``` r
str(d)
```
``` r
    ## 'data.frame':    2 obs. of  2 variables:
    ##  $ scientists: chr  "Einstein" "Newton"
    ##  $ born      : num  1879 1642
```
### <span style="color:#E74C3C">Filtering</span>

Let's take a look at how to filter data in a data frame:

``` r
cars <- cars[c("mpg", "hp", "wt","cyl")]
head(cars)
```
``` r
    ##                    mpg  hp    wt cyl
    ## Mazda RX4         21.0 110 2.620   6
    ## Mazda RX4 Wag     21.0 110 2.875   6
    ## Datsun 710        22.8  93 2.320   4
    ## Hornet 4 Drive    21.4 110 3.215   6
    ## Hornet Sportabout 18.7 175 3.440   8
    ## Valiant           18.1 105 3.460   6
```
``` r
cars[cars$cyl == 8,]
```
``` r
    ##                      mpg  hp    wt cyl
    ## Hornet Sportabout   18.7 175 3.440   8
    ## Duster 360          14.3 245 3.570   8
    ## Merc 450SE          16.4 180 4.070   8
    ## Merc 450SL          17.3 180 3.730   8
    ## Merc 450SLC         15.2 180 3.780   8
    ## Cadillac Fleetwood  10.4 205 5.250   8
    ## Lincoln Continental 10.4 215 5.424   8
    ## Chrysler Imperial   14.7 230 5.345   8
    ## Dodge Challenger    15.5 150 3.520   8
    ## AMC Javelin         15.2 150 3.435   8
    ## Camaro Z28          13.3 245 3.840   8
    ## Pontiac Firebird    19.2 175 3.845   8
    ## Ford Pantera L      15.8 264 3.170   8
    ## Maserati Bora       15.0 335 3.570   8
```
``` r
cars[,c("mpg", "hp")][cars$wt <= 4,]
```
``` r
    ##                    mpg  hp
    ## Mazda RX4         21.0 110
    ## Mazda RX4 Wag     21.0 110
    ## Datsun 710        22.8  93
    ## Hornet 4 Drive    21.4 110
    ## Hornet Sportabout 18.7 175
    ## Valiant           18.1 105
    ## Duster 360        14.3 245
    ## Merc 240D         24.4  62
    ## Merc 230          22.8  95
    ## Merc 280          19.2 123
    ## Merc 280C         17.8 123
    ## Merc 450SL        17.3 180
    ## Merc 450SLC       15.2 180
    ## Fiat 128          32.4  66
    ## Honda Civic       30.4  52
    ## Toyota Corolla    33.9  65
    ## Toyota Corona     21.5  97
    ## Dodge Challenger  15.5 150
    ## AMC Javelin       15.2 150
    ## Camaro Z28        13.3 245
    ## Pontiac Firebird  19.2 175
    ## Fiat X1-9         27.3  66
    ## Porsche 914-2     26.0  91
    ## Lotus Europa      30.4 113
    ## Ford Pantera L    15.8 264
    ## Ferrari Dino      19.7 175
    ## Maserati Bora     15.0 335
    ## Volvo 142E        21.4 109
```

---

# Factor
<!---------------------------------------------------------->
<!---------------------------------------------------------->

### <span style="color:#E74C3C">Introduction</span>

The motivation for factors comes from the concept of categorical data in statistics. An R `factor` may be viewed as a vector with more information added. The extra information consists of a record of the distinct values on that vector, called levels.

### <span style="color:#E74C3C">Creation</span>

``` r
x <- c(5, 12, 13, 12)
xf <- factor(x)
xf
```
``` r
    ## [1] 5  12 13 12
    ## Levels: 5 12 13
```
The distinct values in xf: 5, 12, and 13 are the levels

``` r
str(xf)
```
``` r
    ##  Factor w/ 3 levels "5","12","13": 1 2 3 2
```
``` r
unclass(xf)
```
``` r
    ## [1] 1 2 3 2
    ## attr(,"levels")
    ## [1] "5"  "12" "13"
```
``` r
length(xf)
```
``` r
    ## [1] 4
```
### <span style="color:#E74C3C">Adding Element</span>

Future new levels can be anticipated as well:

``` r
x <- c(5, 12, 13, 12)
xff <- factor(x, levels = c(5, 12, 13, 88))
xff
```
``` r
    ## [1] 5  12 13 12
    ## Levels: 5 12 13 88
```
``` r
xff[2] <- 88
xff
```
``` r
    ## [1] 5  88 13 12
    ## Levels: 5 12 13 88
```
Although you cannot add a value that doesn't have a level associated with it:

``` r
xff[2] <- 28
```
``` r
    ## invalid factor level, NA generated

### <span style="color:#E74C3C">Remove Element</span>

### <span style="color:#E74C3C">Indexing</span>

### <span style="color:#E74C3C">Filtering</span>

### <span style="color:#E74C3C">Math</span>
```

---

# Table
<!---------------------------------------------------------->
<!---------------------------------------------------------->

### <span style="color:#E74C3C">Introduction</span>

### <span style="color:#E74C3C">Creation</span>

### <span style="color:#E74C3C">Adding Element</span>

### <span style="color:#E74C3C">Remove Element</span>

### <span style="color:#E74C3C">Indexing</span>

### <span style="color:#E74C3C">Filtering</span>

### <span style="color:#E74C3C">Math</span>