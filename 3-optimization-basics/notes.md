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
- `f` is concave if `h` is concavee and nonincreasing, `g`  is convex

### Example: Softmax (Log-sum-exp)

![equation](https://latex.codecogs.com/png.latex?g%28x%29%3Dlog%28%5Csum%5Ek_%7Bi%3D1%7De%5E%7Ba_i%5E%5Ctop%20x%20&plus;b_i%7D%29)

Proof of convexity:

`g` is convex if

![equation](https://latex.codecogs.com/png.latex?f%28x%29%3Dlog%28%5Csum_%7Bi%3D1%7D%5Ek%20e%5E%7Bx_i%7D%29)

is convex (affine composition rule).

Its Hessian matrix is in the form:

![equation](https://latex.codecogs.com/png.latex?%5Cnabla%5E2%20f%28x%29%3Ddiag%28z%29-zz%5E%5Ctop)

This is diagonally dominant, hence positive semidefinite.