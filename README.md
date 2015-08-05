# Five-Variables
---
title: "Five Variable Integral"
author: "Jiyi Jiang"
date: "2015年7月29日"
output: html_document
---



```{r}
set.seed(1)
#define domain

a=1
b=2
d=3

c <- c(1, x1, x2, 0, 0)

f1 <- function(x1) {x1}
f2 <- function(x2) {a(x2)+b}
f3 <- function(x3) {a(x3)**2+b(x3)+d}
f4 <- function(x4) {(x4)**3}
f5 <- function(x5) {(x5)+1}

vector <- c(x3, 1+(x2)**2, 0, 0, 0, 1-(x2)**2, x4, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, (x4)+(x5), 1, (x3)*(x5), 0, 0, 0, 0, 1)

M <- matrix( vector,  nrow=5, ncol=5, byrow = TRUE) 

f <- t(c) %*% M %*% c * f1 *f2 * f3 * f4 * f5

adaptIntegrate(f,lowerLimit = c(0,0,0,0,0), upperLimit = c(1,1,1,1,1))

```


```{r}
x <- c(rnorm(10),0,1)
v <- c(1,1,1,x,1,1,1,1,1)
m <- matrix(v, nrow = 3)
```
