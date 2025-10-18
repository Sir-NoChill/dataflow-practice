# Problem 18: Chained Analysis - Reaching Definitions + Available Expressions (Difficulty: d3)

## Problem Statement

Perform both reaching definitions and available expressions analysis on the following TAC, then use the results together to identify optimization opportunities:

```
B1:  x = 5
     y = x + 3
     z = x * 2
     goto B2

B2:  a = x + 3  // potentially redundant
     if a > 8 goto B3 else goto B4

B3:  x = 10    // redefines x
     b = x + 3  // different x value
     c = z + b
     goto B5

B4:  d = x * 2  // potentially redundant
     e = y + d
     goto B5

B5:  f = x + 3  // which x definition reaches here?
     g = x * 2  // which x definition reaches here?
     result = f + g
     return result
```

## Tasks

1. **Apply reaching definitions analysis** first to understand which definitions reach each program point.

2. **Apply available expressions analysis** to identify which expressions are available.

3. **Combine the analyses**:
   - For expression `x + 3` at different points, which definition of `x` is being used?
   - Can `x * 2` be optimized differently at different program points?
   - Which expressions are both available AND use the same reaching definitions?

4. **Design optimizations**:
   - Which redundant expressions can be eliminated?
   - Where should temporary variables be introduced?
   - Show the optimized code.

5. **Verify the interaction**: Explain how the reaching definitions analysis affects the available expressions analysis results.

## Expected Output Format

- Complete reaching definitions analysis
- Complete available expressions analysis
- Analysis of the interaction between the two
- Step-by-step optimization with justification
- Discussion of why both analyses are needed together