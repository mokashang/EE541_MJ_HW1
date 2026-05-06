# MLP Forward Pass

A two-layer MLP with ReLU hidden activation and a linear output, evaluated by hand
to make every matrix multiply and bias addition explicit.

## Given

- Input: x = [+1, -1]^T
- W1 = [[1, -2], [3, 4]], b1 = [1, 0]^T
- W2 = [[2, 2], [2, -3]], b2 = [0, -4]^T
- Hidden layer activation: ReLU(x) = max(x, 0)
- Output layer: Linear (identity)

## Step 1: Compute hidden layer pre-activation (z1)

z1 = W1 * x + b1

z1 = [[1, -2], [3, 4]] * [[1], [-1]] + [[1], [0]]

First compute W1 * x:
- Row 1: 1*(1) + (-2)*(-1) = 1 + 2 = 3
- Row 2: 3*(1) + 4*(-1) = 3 - 4 = -1

So W1 * x = [[3], [-1]]

Adding b1:
z1 = [[3], [-1]] + [[1], [0]] = [[4], [-1]]

## Step 2: Apply ReLU activation

a1 = ReLU(z1) = [[max(4, 0)], [max(-1, 0)]] = [[4], [0]]

## Step 3: Compute output layer pre-activation (z2)

z2 = W2 * a1 + b2

z2 = [[2, 2], [2, -3]] * [[4], [0]] + [[0], [-4]]

First compute W2 * a1:
- Row 1: 2*(4) + 2*(0) = 8 + 0 = 8
- Row 2: 2*(4) + (-3)*(0) = 8 + 0 = 8

So W2 * a1 = [[8], [8]]

Adding b2:
z2 = [[8], [8]] + [[0], [-4]] = [[8], [4]]

## Step 4: Apply output activation (identity/linear)

a2 = z2 = [[8], [4]]

## Final Answer

**The output activation is [8, 4]^T**
