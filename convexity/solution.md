# Convexity Proofs

Direct proofs that the squared function and any quadratic form `x^T A x` with PSD
`A` are convex, plus a counterexample showing `x^3` is not. The PSD result is the
foundation under quadratic-objective optimization (linear regression, MMSE).

## Definition

A function f(x) is convex if for all x, y and 0 < lambda < 1:
f(lambda*x + (1-lambda)*y) <= lambda*f(x) + (1-lambda)*f(y)

## Part (a): Prove f(x) = x^2 is convex, verify f(x) = x^3 is not convex

### Proving f(x) = x^2 is convex

Need to show: (lambda*x + (1-lambda)*y)^2 <= lambda*x^2 + (1-lambda)*y^2

LHS = (lambda*x + (1-lambda)*y)^2
    = lambda^2*x^2 + 2*lambda*(1-lambda)*x*y + (1-lambda)^2*y^2

RHS = lambda*x^2 + (1-lambda)*y^2

RHS - LHS = lambda*x^2 + (1-lambda)*y^2 - lambda^2*x^2 - 2*lambda*(1-lambda)*x*y - (1-lambda)^2*y^2
          = lambda*(1-lambda)*x^2 + (1-lambda)*lambda*y^2 - 2*lambda*(1-lambda)*x*y
          = lambda*(1-lambda)*(x^2 + y^2 - 2*x*y)
          = lambda*(1-lambda)*(x - y)^2

Since 0 < lambda < 1:
- lambda > 0
- (1-lambda) > 0
- (x - y)^2 >= 0

Therefore RHS - LHS >= 0, which means LHS <= RHS.

**Thus f(x) = x^2 is convex.**

### Verifying f(x) = x^3 is NOT convex

We need to find a counterexample. Let's try x = -2, y = 1, lambda = 0.5:

LHS = f(0.5*(-2) + 0.5*1) = f(-0.5) = (-0.5)^3 = -0.125

RHS = 0.5*f(-2) + 0.5*f(1) = 0.5*(-8) + 0.5*1 = -4 + 0.5 = -3.5

Here LHS = -0.125 > RHS = -3.5, so the convexity inequality is violated!

**Thus f(x) = x^3 is NOT convex.**

## Part (b): Prove f(x) = x^T A x is convex if A is positive semi-definite

Need to show: (lambda*x + (1-lambda)*y)^T A (lambda*x + (1-lambda)*y) <= lambda*(x^T A x) + (1-lambda)*(y^T A y)

Let z = lambda*x + (1-lambda)*y

LHS = z^T A z
    = (lambda*x + (1-lambda)*y)^T A (lambda*x + (1-lambda)*y)
    = lambda^2 * x^T A x + 2*lambda*(1-lambda) * x^T A y + (1-lambda)^2 * y^T A y

Note: x^T A y = y^T A x since A is symmetric (PSD matrices are symmetric).

RHS = lambda * x^T A x + (1-lambda) * y^T A y

RHS - LHS = lambda * x^T A x + (1-lambda) * y^T A y
          - lambda^2 * x^T A x - 2*lambda*(1-lambda) * x^T A y - (1-lambda)^2 * y^T A y

          = lambda*(1-lambda) * x^T A x + (1-lambda)*lambda * y^T A y - 2*lambda*(1-lambda) * x^T A y

          = lambda*(1-lambda) * (x^T A x + y^T A y - 2 * x^T A y)

          = lambda*(1-lambda) * (x^T A x - x^T A y - y^T A x + y^T A y)

          = lambda*(1-lambda) * (x - y)^T A (x - y)

Since A is positive semi-definite: (x - y)^T A (x - y) >= 0 for all x, y.
Since 0 < lambda < 1: lambda*(1-lambda) > 0.

Therefore RHS - LHS >= 0, which means LHS <= RHS.

**Thus f(x) = x^T A x is convex when A is positive semi-definite.**
