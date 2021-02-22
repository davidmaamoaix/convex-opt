# Introduction

## Idea of Optimization

tl;dr: minimizing (or maximizing; they are the same thing) a function.

### Examples of Optimizations
Regressions:
- Least Squares:

![equation](https://latex.codecogs.com/svg.latex?%5Cmin_%5Cbeta%20%5Csum_%7Bi%3D1%7D%5En%28y_i%20-%20x_i%5E%5Ctop%20%5Cbeta%29%5E2)

- Least Absolute Deviations (robust):

![equation](https://latex.codecogs.com/svg.latex?%5Cmin_%5Cbeta%20%5Csum_%7Bi%3D1%7D%5En%7Cy_i%20-%20x_i%5E%5Ctop%20%5Cbeta%7C)

Regularized:
- Lasso (with constraints):

![equation](https://latex.codecogs.com/svg.latex?%5Cmin_%5Cbeta%20%5Csum_%7Bi%3D1%7D%5En%28y_i%20-%20x_i%5E%5Ctop%20%5Cbeta%29%5E2%20%5C%5C%5Ctext%7Bs.t.%7D%20%5Csum_j%5Em%20%7C%5Cbeta_j%7C%20%5Cle%20t)

Classifications:
- Logistic Regression:
- Range Loss (SVMs)

Others:
- Traveling Salesman
- Planning/Discrete Opt.
- MLE

### Not Optimizations
- Boosting
- Ensembles (Random Forests)
- CV

Outputs itself isn't simply optimal in respect to some criterion.

### Example: 2D Fused Lasso
2D fused lasso, or 2D total variation denoising, fits a piecewise constant function over an image:

![equation](https://latex.codecogs.com/svg.latex?%5Cmin_%5Ctheta%20%5Cfrac%7B1%7D%7B2%7D%20%5Csum_%7Bi%3D1%7D%5En%20%28y_i%20-%20%5Ctheta_i%29%20%5E%202%20&plus;%20%5Clambda%20%5Csum_%7B%28i%2C%20j%29%20%5Cin%20E%7D%20%7C%5Ctheta_i%20-%20%5Ctheta_j%7C)

where `lambda` is a hyperparameter to determine the penalty, and `E` is the set of edge from a pixel `i` to all adjacent pixels `j`.

Some methods to approach the 2D fused lasso problem (image on course PPT):
- Specialized Alternating Direction Method of Multipliers (ADMM): fast (structured subproblem)
- Proximal Gradient: slow (poor conditioning)
- Coordinate Descent: slow (large active set)

Conclusion: different algorithms work better in different optimization problems.

### Example: 1D Fused Lasso
1D fused lasso is similar to its 2D equvalent:

![equation](https://latex.codecogs.com/svg.latex?%5Cmin_%5Ctheta%20%5Cfrac%7B1%7D%7B2%7D%20%5Csum_%7Bi%3D1%7D%5En%20%28y_i%20-%20%5Ctheta_i%29%20%5E%202%20&plus;%20%5Clambda%20%5Csum_%7Bi%3D1%7D%5E%7Bn%20-%201%7D%20%7C%5Ctheta_i%20-%20%5Ctheta_%7Bi%20&plus;%201%7D%7C)

Trivially, as  `lambda` decreases, more change points appear. We tune `lambda` to fit the more significant change points.

## Convexity

### Convex Set

`C` is a convex set if

![equation](https://latex.codecogs.com/svg.latex?x%2Cy%20%5Cin%20C%20%5CLongrightarrow%20tx%20&plus;%20%281%20-%20t%29y%20%5Cin%20C)

for `t` in `[0, 1]`.

Example: set of points in a convex shape.

### Convex Function

Convex function is a function that;

- Has a convex domain:

![equation](https://latex.codecogs.com/svg.latex?f%3A%5Cmathbb%7BR%7D%5En%5Cto%5Cmathbb%7BR%7D)

such that

![equation](https://latex.codecogs.com/svg.latex?dom%28f%29%5Csubseteq%5Cmathbb%7BR%7D%5En)

is convex

- The value of a point on the function is less than or equal to the linear equation joined by two surrounding points:

![equation](https://latex.codecogs.com/svg.latex?f%28tx%20&plus;%20%281%20-%20t%29y%29%20%5Cle%20tf%28x%29%20&plus;%20%281%20-%20t%29f%28y%29)

## Optimization Problems

All optimization problems can be written as the following:

![equation](https://latex.codecogs.com/svg.latex?%5Cmin_%7Bx%20%5Cin%20D%7D%20f%28x%29%20%5C%5C%5Ctext%7Bs.t.%7D%5C%3B%20g_i%28x%29%5Cle%200%2C%5C%3Bi%3D1%2C%5Cdots%20m%20%5C%5C%5Ctext%7Band%7D%5C%3Bh_j%28x%29%3D0%2C%5C%3Bj%3D1%2C%5Cdots%20r)

where `D` is the common domain of the 3 functions:

![equation](https://latex.codecogs.com/svg.latex?D%20%3D%20dom%28f%29%20%5Ccap%5Cbigcap_%7Bi%3D1%7D%5Em%20dom%28g_i%29%20%5Ccap%20%5Cbigcap_%7Bj%3D1%7D%5Ep%20dom%28h_j%29)

A convex optimization problem is one such that all `f` (the criterion) and all `g` (the constraints) are convex functions, and all `h` are affine:

![equation](https://latex.codecogs.com/svg.latex?h_j%28x%29%20%3D%20a_j%5E%5Ctop%20x%20&plus;%20b_j%2C%5C%3Bj%3D1%2C%5Cdots%20p)

### Local and Global Minima

In optimization problems, `x` is the local minima if `x` satisfies all the constraints and:

![equation](https://latex.codecogs.com/svg.latex?f%28x%29%20%5Cle%20f%28y%29%20%5C%3B%20%5Ctext%7Bfor%20all%20feasible%20%24y%24%7D%2C%20%5C%3B%5ClVert%20x%20-%20y%20%5CrVert_2%20%5Cle%20%5Crho)

In convex problems, the above constraint is satisfied when `rho` is infinity, or for all feasible `y`.

The local minima in a convex optimization problem is the global minima.