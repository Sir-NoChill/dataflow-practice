# Problem 16: Basic Anticipation Analysis (Difficulty: d3)

## Problem Statement

Perform anticipation analysis (also called "anticipated expressions") on the following TAC to identify expressions that will be computed later on all paths:

```
B1:  a = input()
     b = 10
     if a > 0 goto B2 else goto B3

B2:  c = a + b
     d = a * 2
     goto B4

B3:  e = a + b
     f = b * 3
     goto B4

B4:  g = a + b
     h = a * 2
     if g > 15 goto B5 else goto B6

B5:  i = a * 2
     j = i + g
     goto B7

B6:  k = a + b
     l = k + h
     goto B7

B7:  result = a + b + a * 2
     return result
```

## Tasks

1. **Define the anticipation analysis framework** by specifying:
   - The domain of the analysis
   - The direction of the analysis
   - The generalized transfer function
   - The boundary value
   - The meet operator
   - The dataflow equation
   - The initialization of nodes

2. **Distinguish from available expressions**: How does anticipation analysis differ from available expressions analysis?

3. **Apply the backward analysis** until convergence.

4. **Optimization opportunities**: Which expressions are anticipated and could benefit from:
   - Early computation
   - Code hoisting
   - Partial redundancy elimination

## Expected Output Format

- Framework definition with clear distinction from available expressions
- Complete backward analysis with IN/OUT sets
- List of anticipated expressions suitable for optimization
- Discussion of how anticipation enables code motion