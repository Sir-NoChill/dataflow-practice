# Problem 1: Basic Reaching Definitions Analysis (Difficulty: d0)

## Problem Statement

Given the following Three Address Code (TAC), perform reaching definitions analysis.

```
B1:  x = 5
     y = x + 2
     goto B2

B2:  z = x * y
     if z > 10 goto B3 else goto B4

B3:  x = z + 1
     goto B4

B4:  y = x - 1
     return y
```

## Tasks

1. **Define the dataflow analysis framework** for reaching definitions by specifying:
   - The domain of the analysis
   - The direction of the analysis
   - The generalized transfer function
   - The boundary value
   - The meet operator
   - The dataflow equation
   - The initialization of nodes

2. **Apply the analysis** by hand using the iterative fixed-point algorithm until convergence.

3. **Show your work** including:
   - The IN and OUT sets for each basic block at each iteration
   - The final converged solution

## Expected Output Format

Present your solution as IN[B] and OUT[B] sets for each basic block B1, B2, B3, B4, showing the step-by-step iterative process until no changes occur.