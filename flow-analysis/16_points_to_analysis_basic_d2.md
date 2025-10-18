# Basic Points-to Analysis

## Problem Statement
Perform points-to analysis on the following code with pointer assignments and dereferences.

## Three-Address Code
```
B1: p = &x
    q = &y
    r = &z
    goto B2
B2: if condition goto B3
    goto B4
B3: p = q
    *p = 42
    goto B5
B4: q = r
    *q = 24
    goto B5
B5: s = p
    t = *s
    *r = t + 10
    return
```

## Tasks
1. Build the points-to graph for all pointer variables
2. Track how points-to relationships change through assignments
3. Analyze the effects of pointer dereferences on memory locations
4. Determine which memory locations might be modified
5. Identify potential aliasing relationships

## Expected Output Format
- Initial points-to relationships
- Points-to graph evolution through each basic block
- Memory location modification analysis
- Aliasing pairs identification
- Summary of all possible points-to relationships at each program point