Frank Fichtenmueller  
28/10/20162015  

# Quiz 1
## Question 1

Consider influenza epidemics for two parent heterosexual families. Suppose that the probability is 17% that at least one of the parents has contracted the disease. The probability that the father has contracted influenza is 12% while the probability that both the mother and father have contracted the disease is 6%. What is the probability that the mother has contracted influenza?

### Answer

$P(A \cup B) = .17$

$P(A) = .12$

$P(A \cap B) = .06$

$P(A \cup B) = P(A) + P(B) - P(A \cap B)$ 

filling in the values:

$.17 = .12 + P(B) - .06$

$P(B) = $

```r
 .17 - .12  + .06
```

```
## [1] 0.11
```

---

## Question 2

A random variable, X is uniform, a box from 0 to 1 of height 1. (So that its density is f(x)=1 for 0â¤xâ¤1.) What is its 75th percentile? 

### Answer

This density looks like a box. So, notice that $P(X \leq x) = width\times height = x$.
We want 75th percentile: $.75 = P(X\leq x) = x$.


```r
qunif(p=0.75, min=0, max=1)
```

```
## [1] 0.75
```

---

## Question 3

You are playing a game with a friend where you flip a coin and if it comes up heads you give her X dollars and if it comes up tails she gives you Y dollars. The probability that the coin is heads is p (some number between 0 and 1.) What has to be true about X and Y to make so that both of your expected total earnings is 0. The game would then be called âfairâ. 

### Answer

The earnings for all the 'heads up' events should total to 0 when subtracted from the loses from the 'tails up' event. 
So by subtracting the multiplication $X$ with $p$ and $Y$ with $1-p$ from each other, the total should be 0
Rewritten it gives the following result

$X \times p - Y \times (1 - p) = 0$

$X \times p = Y \times (1 - p)$

$\frac{p}{(1 - p)} = \frac{Y}{X}$

---

## Question 4

A density that looks like a normal density (but may or may not be exactly normal) is exactly symmetric about zero. (Symmetric means if you flip it around zero it looks the same.) What is its median?

### Answer

The median must be 0, because 50% of the probability is below 0 and 50% is above 0, when the density is symmetric at zero.

---

## Question 5

Consider the following PMF shown below in R

```r
x <- 1:4
p <- x/sum(x)
temp <- rbind(x, p)
rownames(temp) <- c("X", "Prob")
temp
```

```
##      [,1] [,2] [,3] [,4]
## X     1.0  2.0  3.0  4.0
## Prob  0.1  0.2  0.3  0.4
```

What is the mean? 

### Answer

The center of mass of data is the empirical mean
$\bar X = \sum\limits_{i=1}^n x_ip(x_i)$

The mean is the sum of the x and with it's related probability


```r
Xmean <- sum(temp["X",] * temp["Prob",])
Xmean
```

```
## [1] 3
```

---

## Question 6

A [web site](www.medicine.ox.ac.uk/bandolier/band64/b64-7.html) for home pregnancy tests cites the following: âWhen the subjects using the test were women who collected and tested their own samples, the overall sensitivity was 75%. Specificity was also low, in the range 52% to 75%.â Assume the lower value for the specificity. Suppose a subject has a positive test and that 30% of women taking pregnancy tests are actually pregnant. What number is closest to the probability of pregnancy given the positive test?

### Answer

The answer lies in Bayes' formula

$P(pregnant\:\vert\: +) = \frac{P(+\vert pregnant)P(pregnant)}{P(+\vert pregnant)P(pregnant) \:+\:P(+\vert pregnant^c)P(pregnant^c)}$



The prevalance of pregnancy in the population  is 30%

$P(pregnant) = 0.30$

$P(pregnant^c) = 1 - P(pregnant) = 0.70$



The sensitivity is 75%, eg. the probablility of a positive test when pregnant

$P(+\:\vert\:pregnant) = 0.75$



The specificity is 52%, eg. the probablility of a negative test when not pregnant

$P(-\:\vert\:pregnant^c) = 0.52$

$P(+\:\vert\:pregnant^c) = 1 -  P(-\:\vert\:pregnant^c) = 0.48$



Filling in the values

$P(pregnant\:\vert\: +) = \frac{0.75 \times 0.30}{0.75 \times 0.30 \:+\:0.48 \times 0.70} = $




```r
Ppregnant_pos = 0.75*0.30/(0.75*0.30+0.48*0.70)
round(Ppregnant_pos*100)
```

```
## [1] 40
```
