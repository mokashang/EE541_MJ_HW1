# Problem 3: Hyperplane Distance

## Part (a): Distance from point x0 to hyperplane w^T x + b = 0

The optimization problem is:
min_x ||x0 - x||_2  subject to  w^T x + b = 0

### Derivation using Lagrangian

L(x, lambda) = ||x0 - x||_2^2 + lambda(w^T x + b)

Note: We minimize the squared distance (equivalent problem).

Taking gradient with respect to x and setting to zero:
dL/dx = -2(x0 - x) + lambda * w = 0
=> x0 - x = (lambda/2) * w
=> x = x0 - (lambda/2) * w

Substituting into constraint w^T x + b = 0:
w^T (x0 - (lambda/2) * w) + b = 0
w^T x0 - (lambda/2) * ||w||^2 + b = 0
(lambda/2) * ||w||^2 = w^T x0 + b
lambda/2 = (w^T x0 + b) / ||w||^2

The optimal point on the hyperplane:
x* = x0 - ((w^T x0 + b) / ||w||^2) * w

The distance is:
||x0 - x*||_2 = ||((w^T x0 + b) / ||w||^2) * w||_2
             = |w^T x0 + b| / ||w||^2 * ||w||_2
             = |w^T x0 + b| / ||w||_2

## Answer (Part a)

**Distance = |w^T x0 + b| / ||w||_2**

## Part (b): Distance between two parallel hyperplanes

Given: w^T x + b1 = 0 and w^T x + b2 = 0

These are parallel hyperplanes (same normal vector w).

Pick any point x0 on the first hyperplane: w^T x0 + b1 = 0
=> w^T x0 = -b1

Distance from x0 to the second hyperplane:
d = |w^T x0 + b2| / ||w||_2
  = |-b1 + b2| / ||w||_2
  = |b2 - b1| / ||w||_2

## Answer (Part b)

**Distance = |b2 - b1| / ||w||_2**
