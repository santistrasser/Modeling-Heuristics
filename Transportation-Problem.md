# Transportatin problem

```r

library(lpSolve)

Transport <- data.frame(Leftcolumn <- c("origin_a","origin_b","demand")

cost_dest_1 <- c(8, 2, 40)

cost_dest_2 <- c(6, 4,35)

destination_3 <- c(3, 9, 25)

capacity <- c(70, 40, "Null"))

```
## Defining parameters

Origins run from 1:m where m=2, in this case

Destinations run from 1:j where j=3,  in this case

We wish to minimize the shipping costs 

8xa1 +6xa2 + 3xa3 + 2xb1 + 4xb2 + 9xb3

```r

obj.fun <- c(8, 6, 3, 2, 4, 9)

m <- 2
n <- 3

```

## Build our constraint matrix

```r

constr <- matrix(0, m+n, m*n)

for(i in 1:m){
  for(j in 1:n){constr[i, n*(i-1) + j] <- 1
                constr[m+j, n*(i-1) +j] <- 1
                }
}

```

## Let's code up the varying equalities

```r

const.dir <- c(rep("<=", m), rep(">=", n))

rhs <- c(70, 40, 40, 35, 25)

Now lets solve this model

```r

library(lpSolve)

prod.trans <- lp("min", obj.fun, constr, const.dir, rhs, compute.sens = TRUE)

lp("min", obj.fun, constr, const.dir, rhs, compute.sens = TRUE)

prod.trans$objval
prod.trans$objective
prod.trans$duals.from
prod.trans$duals.to

sol <- matrix(prod.trans$solution, m, n, byrow = TRUE)

lp("min", obj.fun, constr, const.dir, rhs, compute.sens = TRUE)$solution

```

Recal how our listing went for variables

a1, a2, a3, b1, b2, b3

thus the solutions are a2 = 35, a3 = 25, and b1 = 40 : )

## Sensitivity analysis of the lp

```r

prod.trans$duals.from
prod.trans$duals.to
prod.trans$sens.coef.from
prod.trans$sens.coef.to

```
