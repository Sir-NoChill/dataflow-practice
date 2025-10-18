# Problem 44: Range Analysis (Difficulty: d3)

## Problem Statement

Perform range analysis to track variable value ranges:

```
B1:  x = input()     // x in range [0, 100]
     y = 5
     goto B2

B2:  if x > 50 goto B3 else goto B4

B3:  z = x - 25     // what range is z?
     goto B5

B4:  z = x + 10     // what range is z?
     goto B5

B5:  w = z * y      // what range is w?
     array[w] = 1    // bounds check needed?
     return w
```

## Tasks

1. **Define range analysis framework** with interval arithmetic.

2. **Track value ranges** through operations and control flow.

3. **Determine array bounds safety**.

## Expected Output Format

- Range tracking results
- Bounds safety analysis
- Optimization opportunities