# Problem 7: Basic Live Variable Analysis (Difficulty: d1)

## Problem Statement

Perform live variable analysis on the following TAC to determine which variables are live at each program point:

```
B1:  a = 5
     b = a + 3
     c = b * 2
     if c > 10 goto B2 else goto B3

B2:  d = a + b
     e = c - d
     goto B4

B3:  d = b * c
     f = a + d
     goto B4

B4:  g = d + f
     return g
```

## Tasks

1. **Define the live variable analysis framework** by specifying:
   - The domain of the analysis
   - The direction of the analysis
   - The generalized transfer function
   - The boundary value
   - The meet operator
   - The dataflow equation
   - The initialization of nodes

2. **Identify use and def sets** for each basic block.

3. **Apply the backward iterative algorithm** until convergence.

4. **Determine register allocation needs**: Based on the live variable information, what is the minimum number of registers needed at each program point?

## Expected Output Format

- Use and Def sets for each basic block
- IN/OUT sets for each iteration (working backwards)
- Analysis of maximum simultaneous live variables at any point