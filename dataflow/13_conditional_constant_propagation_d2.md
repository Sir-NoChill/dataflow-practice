# Problem 13: Basic Conditional Constant Propagation (Difficulty: d2)

## Problem Statement

Perform conditional constant propagation analysis on the following TAC:

```
B1:  x = 5
     y = 10
     z = x + y
     if x > 3 goto B2 else goto B3

B2:  a = x * 2
     b = y + a
     goto B4

B3:  a = 20
     c = y - x
     goto B4

B4:  d = a + z
     if a == 10 goto B5 else goto B6

B5:  e = d + 100
     goto B7

B6:  e = d + 200
     goto B7

B7:  result = e + z
     return result
```

## Tasks

1. **Define the conditional constant propagation framework** by specifying:
   - The domain of the analysis (hint: consider TOP, BOTTOM, and constant values)
   - The direction of the analysis
   - The generalized transfer function
   - The boundary value
   - The meet operator
   - The dataflow equation
   - The initialization of nodes

2. **Handle conditional branches**: How does the analysis use the condition `x > 3` to refine constant information?

3. **Apply the analysis** tracking the constant state of each variable through each basic block.

4. **Identify optimization opportunities**:
   - Which branches can be eliminated as unreachable?
   - Which expressions can be replaced with constants?

## Expected Output Format

- Framework definition with lattice explanation
- Variable state mappings for each basic block
- Complete analysis showing constant propagation through conditionals
- List of optimizations enabled by the analysis