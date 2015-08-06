# Five-Variables
---
title: "Five Variable Integral"
author: "Jiyi Jiang"
date: "07/29/2015"
output: html_document
---

```{r}
install.packages(cubature)
install.packages(Ryacas)
```

```{r}
library(Ryacas)

set.seed(1)

#Symbolize variables.

x1 <- Sym("x1")
x2 <- Sym("x2")
x3 <- Sym("x3")
x4 <- Sym("x4")
x5 <- Sym("x5")

#M is the 5 by 5 matrix.

M <-List(List(x3, 1+(x2)^2, 0, 0, 0),
         List(1-(x2)^2, x4, 0, 0, 0),
         List(0, 0, 1, 0, 0),
         List(0, 0, (x4)+(x5), 1, (x3)*(x5)),
         List(0, 0, 0, 0, 1))

#C is the 1 by 5 vector.

C <-List(List(0), List(x1), List(x2), List(0), List(0))

# t is the transpose of C.

tC <- function(x) Sym("Transpose(", x, ")")
t <- List(t(C)) 

##
G <- t * M * C 

#Multiplication of five functions
Multiply=function(a,b,c,d,e){
  force(a)
  force(b)
  force(c)
  force(d)
  force(e)
  function(x1,x2,x3,x4,x5){a(x1)*b(x2)*c(x3)*d(x4)*e(x5)}
}

# I used specific coefficient, there is problem on running the function with unspecified coefficient.
f1 <- function(x1) {x1}
f2 <- function(x2) {(x2)+1}
f3 <- function(x3) {(x3)**2+(x3)+4}
f4 <- function(x4) {(x4)**3}
f5 <- function(x5) {(x5)+1}
f=Multiply(f1,f2,f3,f4,f5)


final.function <- G*f

# This step will not work unless you give variable values.
library(cubature)
#adaptIntegrate(f,lowerLimit = c(0,0,0,0,0), upperLimit = c(1,1,1,1,1))

```

