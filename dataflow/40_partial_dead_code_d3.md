# Problem 40: Partial Dead Code Elimination (Difficulty: d3)

## Problem Statement

Eliminate partially dead code:

```
B1:  a = expensive_computation()
     if condition() goto B2 else goto B3

B2:  b = a + 1    // a is used
     goto B4

B3:  c = 5        // a is not used
     goto B4

B4:  return b + c  // a is partially dead in B1
```

## Tasks

1. **Define partial dead code analysis**.

2. **Identify where to insert computations** to eliminate partial deadness.

3. **Show the optimized code**.

## Expected Output Format

- Partial deadness analysis
- Code motion strategy
- Optimized result