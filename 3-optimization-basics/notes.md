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