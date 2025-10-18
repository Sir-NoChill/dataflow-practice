# Problem 4: Basic Available Expressions Analysis (Difficulty: d1)

## Problem Statement

Given the following TAC, perform available expressions analysis to identify common subexpressions:

```
B1:  a = x + y
     b = x * z
     c = x + y
     if a > 10 goto B2 else goto B3

B2:  d = x + y
     e = z * 2
     goto B4

B3:  f = x * z
     g = y + z
     goto B4

B4:  h = x + y
     i = x * z
     return h + i
```

## Tasks

1. **Define the available expressions framework** by specifying:
   - The domain of the analysis
   - The direction of the analysis
   - The generalized transfer function
   - The boundary value
   - The meet operator
   - The dataflow equation
   - The initialization of nodes

2. **Identify all expressions** in the program that could be available.

3. **Compute kill and gen sets** for each basic block.

4. **Apply the iterative algorithm** until convergence.

5. **Identify optimization opportunities**: Which expressions are redundant and could be eliminated?

## Expected Output Format

- List of all expressions considered
- Kill and Gen sets for each basic block
- IN/OUT sets for each iteration
- List of redundant expressions that could be optimized