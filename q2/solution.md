# Problem 2: Partial Derivatives and Optimization

## Given

f(x, y) = 4x^2 + y^2 - xy - 13x

## Part (a): Find partial derivatives

### Partial derivative with respect to x

df/dx = d/dx(4x^2 + y^2 - xy - 13x)
      = 8x + 0 - y - 13
      = 8x - y - 13

### Partial derivative with respect to y

df/dy = d/dy(4x^2 + y^2 - xy - 13x)
      = 0 + 2y - x - 0
      = 2y - x

## Part (b): Find (x, y) that minimizes f

To find the minimum, set both partial derivatives equal to zero:

From df/dx = 0:
8x - y - 13 = 0
=> y = 8x - 13  ... (1)

From df/dy = 0:
2y - x = 0
=> x = 2y  ... (2)

Substituting (2) into (1):
y = 8(2y) - 13
y = 16y - 13
-15y = -13
y = 13/15

From (2):
x = 2 * (13/15) = 26/15

### Verify this is a minimum using the Hessian

H = [[d^2f/dx^2, d^2f/dxdy], [d^2f/dydx, d^2f/dy^2]]
  = [[8, -1], [-1, 2]]

- d^2f/dx^2 = 8 > 0
- det(H) = 8*2 - (-1)*(-1) = 16 - 1 = 15 > 0

Since d^2f/dx^2 > 0 and det(H) > 0, this is indeed a minimum.

## Final Answer

**The minimum occurs at (x, y) = (26/15, 13/15)**
