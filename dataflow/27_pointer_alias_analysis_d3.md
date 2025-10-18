# Problem 27: Pointer Alias Analysis (Difficulty: d3)

## Problem Statement

Perform alias analysis on the following TAC with pointer operations:

```
B1:  p = &x
     q = &y
     r = p
     goto B2

B2:  if input() > 0 goto B3 else goto B4

B3:  p = q      // p and q now alias
     *p = 10    // modifies what p points to
     goto B5

B4:  r = &z
     *r = 20    // modifies what r points to
     goto B5

B5:  a = *p     // what does p point to?
     b = *q     // what does q point to?
     c = *r     // what does r point to?
     d = x + y + z
     return d
```

## Tasks

1. **Define alias analysis framework** by specifying:
   - The domain of the analysis (points-to sets)
   - The direction of the analysis
   - The generalized transfer function for pointer operations
   - The boundary value
   - The meet operator
   - The dataflow equation
   - The initialization of nodes

2. **Apply alias analysis** tracking which pointers may point to which variables.

3. **Analyze the effects of pointer assignments** and how they create or break aliases.

4. **Use alias information** to determine:
   - Which variables may be modified by pointer dereferences
   - What values are loaded by pointer dereferences in B5

5. **Optimization implications**: How does alias analysis affect other dataflow analyses like reaching definitions?

## Expected Output Format

- Alias analysis framework definition
- Points-to sets for each program point
- Analysis of pointer operations and their effects
- Discussion of how aliasing affects optimization