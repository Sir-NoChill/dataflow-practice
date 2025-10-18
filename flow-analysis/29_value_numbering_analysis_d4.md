# Global Value Numbering Analysis

## Problem Statement
Implement global value numbering to detect equivalent expressions across basic block boundaries.

## Three-Address Code
```
B1: a = x + y
    b = x + y
    c = a * 2
    if condition goto B3
    goto B2
B2: d = x + y          // equivalent to a, b
    e = d * 2          // equivalent to c
    f = e + 1
    goto B4
B3: g = a * 2          // equivalent to c
    h = z - w
    d = x + y          // equivalent to a, b
    goto B4
B4: i = d * 2          // equivalent to c, e, g
    j = i + f          // f may not be available
    k = h + 1          // h may not be available
    return j + k
```

## Tasks
1. Assign value numbers to expressions based on their operands
2. Track value number propagation across basic blocks
3. Identify expressions with identical value numbers
4. Handle conditional availability of expressions
5. Generate optimized code using value numbering results

## Expected Output Format
- Value number assignments for each expression
- Value number propagation through the CFG
- Identification of equivalent expressions
- Availability analysis for optimization
- Optimized code with redundant computations eliminated