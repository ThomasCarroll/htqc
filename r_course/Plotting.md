Plotting in R
========================================================
author: SANJAY KHADAYATE
date: 02/02/2015

========================================================

1.  Introduction

2.	Base graphics
  + Line Charts
  + Bar Charts
  + Histograms
  + Pie Charts
  + Dot charts
  + Combining Plots
     
3.  Saving your plot

4.	Lattice R package

5.	ggplot2 R package


Introduction
========================================================
R has excellent graphics and plotting capabilities. They are mostly found in following three sources.
 + base graphics
 + the lattice package
 +  the ggplot2 package
 
Lattice and ggplot2 packages are built on grid graphics package while the base graphics routines adopt a pen and paper model for plotting.


Base Graphics
========================================================
+ Line Charts

First we'll produce a very simple graph using the values in the treatment vector:


```r
treatment <- c(0.02,1.8, 17.5, 55,75.7, 80)
```

Plot the treatment vector with default parameters


```r
plot(treatment)
```

Line Plot
========================================================

![plot of chunk unnamed-chunk-3](Plotting-figure/unnamed-chunk-3.png) 

=======================================================
Now, let's add a title, a line to connect the points, and some color:

Plot treatment using blue points overlayed by a line


```r
plot(treatment, type="o", col="blue")
```
Create a title with a red, bold/italic font

```r
title(main="Treatment", col.main="red", font.main=4)
```

Line Plot
========================================================
![plot of chunk unnamed-chunk-6](Plotting-figure/unnamed-chunk-6.png) 

========================================================
Now let's add a red line for a control vector and specify the y-axis range directly so it will be large enough to fit the data:

Define control vector

```r
control <- c(0, 20, 40, 60, 80,100)
```

Plot treatment using a y axis that ranges from 0 to 100

```r
plot(treatment, type="o", col="blue", ylim=c(0,100))
```
Plot control with red dashed line and square points

```r
lines(control, type="o", pch=22, lty=2, col="red")
```


==========================================================

Create a title with a red, bold/italic font

```r
title(main="Expression Data", col.main="red", font.main=4)
```

![plot of chunk unnamed-chunk-11](Plotting-figure/unnamed-chunk-11.png) 

==========================================================

Next let's change the axes labels to match our data and add a legend. 
We'll also compute the y-axis values using the max function 
so any changes to our data will be automatically 
reflected in our graph. 

Calculate range from 0 to max value of data

```r
g_range <- range(0, treatment, control)
```

range returns a vector containing the minimum and maximum of all the given arguments.

Plot treatment using y axis that ranges from 0 to max value in treatment or control vector.  Turn off axes and annotations (axis labels) so we can specify them ourselves.

========================================================


```r
plot(treatment, type="o", col="blue", ylim=g_range,axes=FALSE, ann=FALSE)
```

Make x axis using labels


```r
axis(1, at=1:6, lab=c("Mon","Tue","Wed","Thu","Fri","Sat"))
```

Make y axis with horizontal labels that display ticks at every 20 marks. 


```r
axis(2, las=1, at=20*0:g_range[2])
```

Create box around plot


```r
box()
```

========================================================

![plot of chunk unnamed-chunk-17](Plotting-figure/unnamed-chunk-17.png) 

========================================================
Calculate range from 0 to max value of data

```r
g_range <- range(0, treatment, control)
```

range returns a vector containing the minimum and maximum of all the given arguments.

Plot treatment using y axis that ranges from 0 to max value in treatment or control vector.  Turn off axes and annotations (axis labels) so we can specify them ourselves.


```r
plot(treatment, type="o", col="blue", ylim=g_range,axes=FALSE, ann=FALSE)
```

========================================================

Make x axis using labels

```r
axis(1, at=1:6, lab=c("Mon","Tue","Wed","Thu","Fri","Sat"))
```

Make y axis with horizontal labels that display ticks at every 20 marks. 


```r
axis(2, las=1, at=20*0:g_range[2])
```

Create box around plot

```r
box()
```

========================================================

Plot control vector with red dashed line and square points


```r
lines(control, type="o", pch=22, lty=2, col="red")
```

Create a title with a red, bold/italic font

```r
title(main="Data", col.main="red", font.main=4)
```

Label the x and y axes with dark green text

```r
title(xlab="Days", col.lab=rgb(0,0.5,0))
title(ylab="Values", col.lab=rgb(0,0.5,0))
```

========================================================

Create a legend at (1, g_range[2]) that is slightly smaller (cex) and uses the same line colors and points used by the actual plots 


```r
legend(1, g_range[2], c("treatment","control"), cex=0.8, col=c("blue","red"), pch=21:22, lty=1:2);  
```

![plot of chunk unnamed-chunk-27](Plotting-figure/unnamed-chunk-27.png) 
 	
	
========================================================	
	
Bar Charts
Let's start with a simple bar chart graphing the treatment vector: 
Plot treatment


```r
barplot(treatment)
```

![plot of chunk unnamed-chunk-29](Plotting-figure/unnamed-chunk-29.png) 

========================================================
 
Let's now read the data from the example.txt data file, add labels, blue borders around the bars, and density lines: 

Read values from tab-delimited example.txt









































































































































```
Error in file(file, "rt") : cannot open the connection
```
