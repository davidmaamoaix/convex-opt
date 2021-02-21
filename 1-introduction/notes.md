# Introduction

## Idea of Optimization

tl;dr: minimizing a function.

### Examples of Optimizations
Regressions:
- Least Squares
- Least Absolute Deviations (robust)

Regularized:
- Lasso (with constraints)

Classifications:
- Logistic Regression
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
2D fused lasso, or 2D total variation denoising:
![equation](https://latex.codecogs.com/svg.latex?%5Cmin_%5Ctheta%20%5Cfrac%7B1%7D%7B2%7D%20%5Csum_%7Bi%3D1%7D%5En%20%28y_i%20-%20%5Ctheta_i%29%20%5E%202%20&plus;%20%5Clambda%20%5Csum_%7B%28i%2C%20j%29%20%5Cin%20E%7D%20%7C%5Ctheta_i%20-%20%5Ctheta_j%7C)