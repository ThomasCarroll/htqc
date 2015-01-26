Introduction to R, Day 2
========================================================
author: Thomas Carroll
date: 
css:style.css
autosize:true
autosize:true
Recap -- 
========================================================

Control Structure and Loops
========================================================
We have looked at using logical vectors as a versatile way to index other data types

```r
x <- 1:10
x[x < 4]
```

```
[1] 1 2 3
```

Logicals have an important part in controlling how scripted procedures execute.


Two important control structures
========

- Conditional branching (if,else ifelse)
- Loops (for, while, switch)

**While** I'm analysing data, **if** I need to execute complex statistical procedures on the data I will use R **else** I will use a calculator.

Conditional Branching.
========

Conditional Branching is evaluation of a logical to determine whether a procedure is executed.

In the R we use the **if** statement with the logical to be evaluated in **()** and dependent statement to executed in **{}**.


```r
x <- T
x
```

```
[1] TRUE
```

```r
if(x){
  message("x is true")
}
```

```
x is true
```

```r
x <- F
x
```

```
[1] FALSE
```

```r
if(x){
  message("x is true")
}
```
Evaluating in if() statments
====

More often, we construct the logical value within **()** itself.


```r
x <- 10
y <- 4
x > y
```

```
[1] TRUE
```

```r
if(x > y){
  message("The value of x is ",x," is greater than ", y)
}
```

```
The value of x is 10 is greater than 4
```
Here the message is printed because x is greater than y. 

```r
y <- 20
if(x > y){
  message("The value of x is ",x," is greater than ", y)
}
```
Here, x is not longer greater than y so no message is printed.

We really still want a message telling us what was the result of the comparison even if it didn't pass criteria

else following an if().
========================

If we want to perform an operation when the condition is false we can follow the if() statement with an else statement.


```r
x < - 10
```

```
[1] FALSE
```

```r
if(x < 5){
  message(x, " is less than to 5")
   }else{
     message(x," is greater than or equal to 5")
}
```

```
10 is greater than or equal to 5
```

```r
x <- 3
if(x < 5){
  message(x, " is less than 5")
   }else{
     message(x," is greater than or equal to 5")
}
```

```
3 is less than 5
```



ifelse()
===========

We may wish to execute different procedures under multiple conditions. This can be control in R using the else if() following an initial if() statement.

```r
x <- 5
if(x > 5){
  message(x," is greater than 5")
  }else if(x == 5){
    message(x," is 5")
  }else{
    message(x, " is less than 5")
  }
```

elseif()
======

A useful function to evaluate condition statements over vectors is the ifelse() function.


```r
x <- 1:10
message(x)
```

The ifelse() functions take the arguments of the condition to evaluate, the action if the condition is true and the action when condition is false.


```r
ifelse(x <= 3,"lessOrEqual","more") 
```

```
 [1] "lessOrEqual" "lessOrEqual" "lessOrEqual" "more"        "more"       
 [6] "more"        "more"        "more"        "more"        "more"       
```

This allows for multiple nested else if statements to be applied to vectors.


```r
ifelse(x == 3,"same",
       ifelse(x < 3,"less","more")
       ) 
```

```
 [1] "less" "less" "same" "more" "more" "more" "more" "more" "more" "more"
```
Loops
======

The two main generic methods of looping in R are **while** and **for**

- **while** - *while* loops repeat the execution of code while a condition evaluates as false.

- **for** - *for* loops repeat the execution of code for a range of specified values.

While loops
=====

While loops are most useful if you know the condition will be satisified but are not sure when. (i.e. Looking for a when a number first occurs in a list).

```r
i <- 0
x <- 1
while(x != 3){
  message(x[i])
  x <- x+1
}
message("Finally x is 3")
```

For loops
=====


For loops allow the user to cycle through a range of values applying an operation for every value.
.
Here we cycle through x and print out its value

```r
x <- 1:10
for(i in x){
  message(i)
}
```


Looping through indices
=====

In sme occasions we may wish to keep track of the position in x we are evaluating. A common pactice is loop though all possible index positions of x using the expression **1:length(x)**.


```r
x <- sample(1:24,5)
y <- letters
1:length(x)
```

```
[1] 1 2 3 4 5
```

```r
for(i in 1:length(x)){
  message("Number ",i," in x is ",x[i])
  message("Letter ",i," in the alphabet is ",y[i]) 
}
```

```
Number 1 in x is 9
Letter 1 in the alphabet is a
Number 2 in x is 6
Letter 2 in the alphabet is b
Number 3 in x is 22
Letter 3 in the alphabet is c
Number 4 in x is 4
Letter 4 in the alphabet is d
Number 5 in x is 7
Letter 5 in the alphabet is e
```

Loops and conditionals
=======================

Loops can be combined with conditional statements to allow for complex control of their execution over R objects. 


```r
x <- 1:13

for(i in 1:13){
  if(i > 10){
    message("Number ",i," is greater than 10")
  }else if(i == 10){
    message("Number ",i," is  10") 
  }else{
    message("Number ",i," is less than  10") 
  }
}
```

Breaking loops
=====

We can use conditionals to exit a loop if a condition is satisfied, just a while loop.


```r
x <- 1:13

for(i in 1:13){
  if(i < 10){
    message("Number ",i," is less than 10")
  }else if(i == 10){
    message("Number ",i," is  10")
    break
  }else{
    message("Number ",i," is greater than  10") 
  }
}
```

```
Number 1 is less than 10
Number 2 is less than 10
Number 3 is less than 10
Number 4 is less than 10
Number 5 is less than 10
Number 6 is less than 10
Number 7 is less than 10
Number 8 is less than 10
Number 9 is less than 10
Number 10 is  10
```

Functions
===

As we have seen, a function is command which require one or more arguments and returns a single R object. 

This allows for the user to perform complex calculations and prodecures with one simple operation.


```r
x=rnorm(100,70,10)
y <- jitter(x,amount=1)+20
mean(x)
```

```
[1] 69.87458
```

```r
lmExample <- data.frame(X=x,Y=y)
lmResult <- lm(Y~X,data=lmExample)
```
***

```r
plot(Y~X,data=lmExample,main="Line of best fit with lm()",
     xlim=c(0,150),ylim=c(0,150))
abline(lmResult,col="red",lty=3,lwd=3)
```

![plot of chunk unnamed-chunk-16](introToR_Day2-figure/unnamed-chunk-16-1.png) 


Defining your own functions
======

Although we have access to many built functions in R, there will be many complex tasks we wish to perform regularly which are particular to our own work and for which no suitable function exists. 

For these tasks we can construct your own functions with **function()**

To define a function we need to define 
- the argument names within **()**
- the expression to be evaluated within **{}** 
- the variable the function will be assigned to with **<-**.
- the data that should be output from the function using **return()** 

**Function_name** <- function(**Argument1**,**Argument2**){ **Expression**}


```r
myFirstFunction <- function(myArgument1,myArgument2){
  myResult <- (myArgument1*myArgument2)
  return(myResult)
}
myFirstFunction(4,5)
```

```
[1] 20
```

User functions extend the
capabilities of R by adapting or creating new tasks that are tailored
to your specific requirements.

Default arguments
====

In some functions a default value for an argument may be used.
This allows the function to provide a value for an argument when the user does not specify one.

Default arguments can be specified by assigning a value

```r
mySecondFunction <- function(myArgument1,myArgument2=10){
  myResult <- (myArgument1*myArgument2)
  return(myResult)
}
mySecondFunction(4,5)
```

```
[1] 20
```

```r
mySecondFunction(4)
```

```
[1] 40
```


Missing Arguments
====

In some cases a function may wish to deal with missing arguments in a different way to setting a generic default for the argument. The missing() function can be used to evaluate whether an argument has been defined 


```r
mySecondFunction <- function(myArgument1,myArgument2){
  if(missing(myArgument2)){
    message("Value for myArgument2 not provided so will square myArgument1")
    myResult <- myArgument1*myArgument1
  }else{
    myResult <- (myArgument1*myArgument2)   
  }
  return(myResult)
}
mySecondFunction(4,5)
```

```
[1] 20
```

```r
mySecondFunction(4)
```

```
Value for myArgument2 not provided so will square myArgument1
```

```
[1] 16
```


Returning objects from functions
====

We have seen a function returns the value within the return() function.If no return is specified, the result of last line evaluated in the function.


```r
myforthFunction <- function(myArgument1,myArgument2=10){
  myResult <- (myArgument1*myArgument2)
  return(myResult)
  print("I returned the result")
}
myfifthFunction <- function(myArgument1,myArgument2=10){
(myArgument1*myArgument2)
}

myforthFunction(4,5)
```

```
[1] 20
```

```r
myfifthFunction(4,5)
```

```
[1] 20
```

Note that the print() statment after the return() is not evaluated in myforthFuntion.

Returning lists from functions
====

The return() function can only return one R object at a time. To return multiple data objects from one function call, a list can be used to contain other data objects.


```r
mySixFunction <- function(arg1,arg2){
  result1 <- arg1*arg2
  result2 <- date()
  return(list(Calculation=result1,DateRun=result2))
}
result <- mySixFunction(10,10)

result
```

```
$Calculation
[1] 100

$DateRun
[1] "Sun Jan 25 21:48:44 2015"
```

```r
c(class(result$Calculation),class(result$DateRun))
```

```
[1] "numeric"   "character"
```

====

If we want to return a mix of different data types back from a function, we will use a list.


Its a good idea to have some simple checking of the arguments you have.
A useful function pt

Defining functions can
- Make code more accessible.
- Streamline repetitive tasks.
- Increase reproducibility. 



Easy to read
x <- 1:40
y <- 5:35

Harder to read



Some tips for speed comparisons..


Getting help
