---
title: "TestConversion"
author: "tcarroll"
date: "25 January 2015"
output:
  ioslides_presentation:
    css: style.css
---

##What is R?


**R** is scripting language and environment for **statistical computing**.

sqrt(25)-1

Developed by [Robert Gentleman](http://www.gene.com/scientists/our-scientists/robert-gentleman) and [Ross Ihaka](https://www.stat.auckland.ac.nz/~ihaka/). 


Inheriting much from its predecessor **S** (Bell labs).

- Open source & cross platform
- Suited to high level data analysis
- Extensive graphics capabilities
- Diverse range of add-on packages
- Active community of developers
- Thorough documentation



##R Basics


type:section

- Simple Calculations
- Intro to variables
- Vectors
- Lists
- Matrices
- Data frames



##Simple Calculations 


type: subsection
At its most basic, **R** can be used as a simple calculator.

```r
> 3+1
```

```
[1] 4
```

```r
> 2*2
```

```
[1] 4
```

```r
> sqrt(25)-1
```

```
[1] 4
```

##Using functions 



The **sqrt(25)** demostrates the use of functions in R.

A function performs a complex operation on it's arguments and returns the result.

In R, arguments are provided to R within the parenthesis that follows function name.

So **sqrt(*ARGUMENT*)** will provide the square root of value of ***ARGUMENT***.

Other examples of functions include **mean()**, **sum()**, **max()**.

```r
mean(2,4,6)
```

```
[1] 2
```

```r
sum(2,4,6)
```

```
[1] 12
```

```r
max(2,4,6)
```

```
[1] 6
```
