# Problem 10: Basic Very Busy Expressions Analysis (Difficulty: d2)

## Problem Statement

Perform very busy expressions analysis on the following TAC to identify expressions that will definitely be computed on all paths:

```
B1:  a = 10
     b = 20
     if a > 5 goto B2 else goto B3

B2:  c = a + b
     d = a * b
     goto B4

B3:  e = a + b
     f = a - b
     goto B4

B4:  g = a + b
     h = d + e
     if g > 15 goto B5 else goto B6

B5:  i = a * b
     j = i + g
     goto B7

B6:  k = a * b
     l = k - g
     goto B7

B7:  result = a + b
     return result
```

## Tasks

1. **Define the very busy expressions framework** by specifying:
   - The domain of the analysis
   - The direction of the analysis
   - The generalized transfer function
   - The boundary value
   - The meet operator
   - The dataflow equation
   - The initialization of nodes

2. **Identify all expressions** that could be very busy.

3. **Apply the backward analysis** until convergence.

4. **Code motion opportunities**: Which expressions are very busy and could be moved earlier in the code for optimization?

## Expected Output Format

- List of all expressions analyzed
- Kill and Gen sets for each basic block
- IN/OUT sets for each iteration working backwards
- List of very busy expressions suitable for code motion