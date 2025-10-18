# Context-Sensitive Interprocedural Analysis

## Problem Statement
Perform context-sensitive constant propagation analysis on the following program with multiple call sites.

## Three-Address Code
```
// Function main
main:
    x = compute(5, 10)
    y = compute(x, 15)
    z = compute(0, y)
    return z

// Function compute(a, b)
compute:
    if a == 0 goto L1
    if b > 10 goto L2
    result = a + b
    return result
L1: result = b * 2
    return result
L2: temp = helper(a)
    result = temp + b
    return result

// Function helper(val)
helper:
    if val > 0 goto L3
    return 1
L3: return val * 3
```

## Tasks
1. Model different calling contexts for the compute function
2. Perform context-sensitive constant propagation
3. Track how constants flow through different call paths
4. Compare results with context-insensitive analysis
5. Identify optimization opportunities enabled by context sensitivity

## Expected Output Format
- Call string or functional approach context representation
- Constant propagation results for each calling context
- Analysis of how context affects precision
- Comparison table: context-sensitive vs context-insensitive results
- Optimization opportunities unique to context-sensitive analysis