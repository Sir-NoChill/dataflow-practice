# Analysis Orchestration and Dependencies

## Problem Statement
Design and execute an analysis pipeline for the following code, considering analysis dependencies and invalidation.

## Three-Address Code
```
B1: p = &array[0]
    q = &array[10]
    x = 5
    y = 10
    goto B2
B2: if x > 0 goto B3
    goto B6
B3: temp = x + y
    if temp > 15 goto B4
    goto B5
B4: *p = temp
    p = p + 1
    x = x - 1
    goto B2
B5: *q = temp
    q = q - 1
    y = y + 1
    goto B2
B6: result = *p + *q
    return result
```

## Tasks
1. Identify required analyses and their dependencies
2. Design an analysis scheduling order
3. Perform the following analyses in correct sequence:
   - CFG construction
   - Dominance analysis
   - Points-to analysis
   - Live variable analysis
   - Available expressions
4. Show how each analysis uses results from its prerequisites
5. Analyze which analyses would need recomputation after loop optimizations

## Expected Output Format
- Analysis dependency graph
- Scheduled analysis execution order
- Results from each analysis phase
- Dependencies between analysis results
- Invalidation analysis for potential transformations