# Linear Programming

## Using lpSolve

### We are going to:
minimize 8y1 + 8y2
subject to
2y1 + y2 >= 300
y1 + 2y2 >= 200
y1, y2 >=0

```r

library(lpSolve)
f.obj<- c(8, 8)
f.con<- matrix(c(2,1,1,2), ncol=2, byrow=T)
f.dir<- c(">=", ">=")
f.rhs<- c(300,200)


lp("min", f.obj, f.con, f.dir, f.rhs)

lp("min", f.obj, f.con, f.dir, f.rhs)$solution

```
