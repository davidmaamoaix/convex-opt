# Optimization Basics

If the Hessian matrix of function `f` is strictly positive definite, then `f` is strictly convex (but not the other way around).

## More Operations Preserving Convexity

### Affine Composition

`f` convex implies

![equation](https://latex.codecogs.com/png.latex?g%28x%29%20%3D%20f%28Ax&plus;b%29)

is convex.

### General Composition

Suppose

![equation](https://latex.codecogs.com/png.latex?f%3Dh%5Ccirc%20g)

, then:
- `f` is convex if `h` is convex and nondecreasing, `g` is convex
- `f` is convex if `h` is convex and nonincreasing, `g` is concave
- `f` is concave if `h` is concave and nondecreasing, `g` is concave
- `f` is concave if `h` is concave and nonincreasing, `g`  is convex

### Example: Softmax (Log-sum-exp)

![equation](https://latex.codecogs.com/png.latex?g%28x%29%3Dlog%28%5Csum%5Ek_%7Bi%3D1%7De%5E%7Ba_i%5E%5Ctop%20x%20&plus;b_i%7D%29)

Proof of convexity:

`g` is convex if

![equation](https://latex.codecogs.com/png.latex?f%28x%29%3Dlog%28%5Csum_%7Bi%3D1%7D%5Ek%20e%5E%7Bx_i%7D%29)

is convex (affine composition rule).

Its Hessian matrix is in the form:

![equation](https://latex.codecogs.com/png.latex?%5Cnabla%5E2%20f%28x%29%3Ddiag%28z%29-zz%5E%5Ctop)

This is diagonally dominant, hence positive semidefinite.

## Optimization Terminology

Recall that a convex optimization problem is:

![equation](https://latex.codecogs.com/png.latex?%5Cmin_%7Bx%5Cin%20D%7D%20f%28x%29%5C%5C%5Ctext%7Bs.t.%7D%5C%3B%20g_i%28x%29%5Cle%200%2C%20i%3D1%2C%5Cdots%20m%3B%20Ax%3Db)

where `f` and all `g` are all convex, and the optimization domain is the intersection of domains of all of them.

- `f` is called the criterion/objective function
- `g_i` is called the inequality constraint function
- If an `x` satisfies all the constraints above then it is called a feasible point
- The minimum of `f(x)` over all feasible points is called the optimal value `f^*`
- If `x` is feasible and `f(x) = f^*`, then `x` is called optimal/solution/minimizer
- If `x` is feasible and `g_i(x) = 0`, then `g_i`  is active at `x`

### Convex Solution Set

Let `X_{opt}` be the set of all solutions to a convex problem:

![equation](https://latex.codecogs.com/png.latex?X_%7Bopt%7D%20%3D%20arg%5Cmin%20f%28x%29%5C%5Cs.t.%5C%3B%20g_i%28x%29%5Cle%200%2C%20i%3D1%2C%5Cdots%20m%3B%20Ax%3Db)

Key property: `X_{opt}` is a convex set

### Example: Lasso

Given:

![equation](https://latex.codecogs.com/png.latex?y%20%5Cin%20%5Cmathbb%7BR%7D%5En%2C%20X%20%5Cin%20%5Cmathbb%7BR%7D%5E%7Bn%5Ctimes%20p%7D)

, consider the lasso problem:

![equation](https://latex.codecogs.com/png.latex?%5Cmin_%5Cbeta%20%5ClVert%20y-X%5Cbeta%20%5CrVert%5E2_2%5C%5C%5Ctext%7Bs.t.%7D%20%5C%3B%20%5ClVert%20%5Cbeta%20%5CrVert_1%20%5Cle%20s)