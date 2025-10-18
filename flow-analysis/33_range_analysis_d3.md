# Range Analysis

## Problem Statement
Implement range analysis to track possible value ranges of integer variables.

## Three-Address Code
```
B1: x = input_bounded(1, 100)    // x ∈ [1, 100]
    y = 0                        // y = 0
    goto B2
B2: if x <= 0 goto B6           // loop condition
B3: if x % 2 == 0 goto B4
    goto B5
B4: y = y + x                   // x is even, x ∈ [2, 100]
    x = x / 2                   // x ∈ [1, 50]
    goto B2
B5: y = y + x + 1              // x is odd, x ∈ [1, 99]
    x = (x - 1) / 2            // x ∈ [0, 49]
    goto B2
B6: z = array_access(arr, y)    // bounds check needed for y?
    return z
```

## Tasks
1. Define range lattice and abstract operations
2. Track range evolution through arithmetic operations
3. Handle range narrowing through conditional branches
4. Analyze range widening at loop merge points
5. Identify array bounds check elimination opportunities

## Expected Output Format
- Range lattice operations definition
- Range propagation through each operation
- Conditional range narrowing analysis
- Loop widening strategy and results
- Bounds check elimination analysis