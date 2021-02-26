# Sets and Functions

## Definitions

Recall that a convex set `C` is a set such that:

![equation](https://latex.codecogs.com/svg.latex?x%2Cy%20%5Cin%20C%20%5CLongrightarrow%20tx%20&plus;%20%281%20-%20t%29y%20%5Cin%20C)

for `t` in `[0, 1]`.

### Convex Combination

The convex combination of

![equation](https://latex.codecogs.com/png.latex?x_1%2C%20%5Cdots%20x_k%20%5Cin%20%5Cmathbb%7BR%7D%5En)

is any linear combination whose coefficients are non-negative and sum to `1`:

![equation](https://latex.codecogs.com/png.latex?%5Ctheta_1%20x_1%20&plus;%20%5Cldots%20&plus;%20%5Ctheta_k%20x_k%5C%5C%5Ctext%7Bs.t.%7D%5C%3B%5Ctheta_i%20%5Cle%200%2C%5C%3Bi%3D1%2C%5Cdots%20k%20%5C%3B%5Ctext%7Band%7D%5C%3B%20%5Csum_%7Bi%3D1%7D%5Ek%20%5Ctheta_i%3D1)

Examples:
- Empty set
- Norm ball
- Hyperplane
- Halfspace
- Affine space

A polyhedron can be constructed by a set of linear inequalities:

![equation](https://latex.codecogs.com/svg.latex?%5C%7Bx%3AAx%5Cle%20b%5C%7D)

Notee that comparisons of vectors in 10-725 is interpreted component-wise:

![equation](https://latex.codecogs.com/svg.latex?a%20%5Cle%20b%20%5Cto%20a_i%20%5Cle%20b_i%5C%3B%5Ctext%7Bfor%20all%7D%5C%3B%20i%3D1%2C%5Cdots%20n)

### Convex Hull

The convex hull of set `C` is all convex combinations of its elements; convex hulls are always convex (even if `C` is not convex).

## Convex Cone

Cones are defined as such:

![equation](https://latex.codecogs.com/svg.latex?x%20%5Cin%20C%20%5CLongrightarrow%20tx%20%5Cin%20C%20%5C%3B%5Ctext%7Bfor%20all%7D%5C%3B%20t%5Cge%200)

Cones are not necessarily convex.

### Example of Convex Cones

Norm cone is define as:

![equation](https://latex.codecogs.com/svg.latex?%5C%7B%28x%2C%20t%29%3A%5ClVert%20x%20%5CrVert%5Cle%20t%5C%7D)

Normal cone (completely different from norm cone despite the name) is always convex, and is defined as:

![equation](https://latex.codecogs.com/svg.latex?N_C%28x%29%20%3D%20%5C%7Bg%3Ag%5E%5Ctop%20x%20%5Cge%20g%5E%5Ctop%20y%5C%7D)

for any `x` and `y` in `C`.

### Related Definitions

- Conic combination: linear combination with all coefficient terms greater or equal to 0:

![equation](https://latex.codecogs.com/png.latex?%5Ctheta_1%20x_1%20&plus;%20%5Cdots%20&plus;%20%5Ctheta_k%20x_k%2C%5C%3B%5Ctext%7Bwith%7D%5C%3B%5Ctheta%20%5Cle%200)

- Conic hull of `C`: all conic combinations of elements in `C`

## Properties of Convex Sets

Some cool properties. Yay!

### Separating Hyperplane Theorem

Two disjoint convex set have a separating hyperplane between them.

Formally, for two disjoint convex set `C` and `D`, there exists `a` and `b` such that:

![equation](https://latex.codecogs.com/svg.latex?C%5Csubseteq%20%5C%7Bx%3Aa%5E%5Ctop%20x%5Cle%20b%5C%7D%2C%20D%5Csubseteq%20%5C%7Bx%3Aa%5E%5Ctop%20x%5Cge%20b%5C%7D)

### Supporting Hyperplane Theorem

A point on the boundary of a convex set has a supporting hyperplane passing through it.

Formally, for non-empty convex set `C` and `x_0` (point on boundary), then there exists `a` such that:

![equation](https://latex.codecogs.com/svg.latex?C%5Csubseteq%20%5C%7Bx%3Aa%5E%5Ctop%20x%5Cle%20a%5E%5Ctop%20x_0%5C%7D)

## Operations Preserving Convexity

- Intersection: the intersection of convex sets is convex
- Scaling and Translation: mapping a convex set with a linear transformation function results in another convex set
- Affine Images and Preimages (same as above) (a preimage is the set of all `x` which, after applying function `f`, lies in `C`)

### Example: Linear Matrix Inequality Solution Set

For a set of matrices `A` and symmetrical matrix `B`, a linear matrix inequality is in the form of:

![equation](https://latex.codecogs.com/png.latex?x_1%20A_1&plus;%5Cdots&plus;x_k%20A_k%20%5Cpreccurlyeq%20B)

where `x` is a vector os size `k`.

Proof of the set `C` of points `x` that satisfy the above inequality is convex:

Consider

![equation](https://latex.codecogs.com/svg.latex?f%3A%5Cmathbb%7BR%7D%5Ek%20%5Cto%20S%5En)

(to be continued)

## Convex Functions

Note that concave functions can be considered convex functions (just apply -1).

### Modifiers

- Strictly convex: strict inequality when interpolating (`0 < t < 1`) between two points on the function:

![equation](https://latex.codecogs.com/svg.latex?f%28tx%20&plus;%20%281-t%29y%29%20%3C%20tf%28x%29%20&plus;%20%281-t%29f%28y%29%20%5C%5C%5Ctext%7Bfor%7D%5C%3B%200%3Ct%3C1)

- Strongly convex: with parameter `m` (`m > 0`), `f` is `m` strongly convex if

![equation](https://latex.codecogs.com/svg.latex?f%28x%29%20-%20%5Cfrac%7Bm%7D%7B2%7D%5ClVert%20x%5CrVert_2%5E2)

is convex (at least as convex as quadratic function).

Therefore, strong convexity implies strict convexity, which implies convexity.