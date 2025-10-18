# Interference Graph Construction with Flow Analysis

## Problem Statement
Build an interference graph considering both live variable analysis and dataflow optimizations.

## Three-Address Code
```
B1: x = a + b
    y = c * d
    temp1 = x + y
    goto B2
B2: if temp1 > 10 goto B3
    goto B4
B3: z = x + 1
    w = y - 1
    temp2 = z * w
    x = temp2
    goto B5
B4: z = x - 1
    w = y + 1
    temp2 = a + b  // common subexpression
    y = temp2
    goto B5
B5: temp3 = x + y
    if temp3 < z goto B6
    goto B7
B6: result = w + z
    x = result
    goto B2
B7: final = x + y + z + w
    return final
```

## Tasks
1. Perform live variable analysis considering common subexpressions
2. Apply available expressions analysis to identify optimization opportunities
3. Build interference graph after applying common subexpression elimination
4. Analyze how dataflow optimizations affect register interference
5. Compare interference graphs before and after optimization

## Expected Output Format
- Live variable analysis with and without CSE optimization
- Available expressions analysis results
- Code after common subexpression elimination
- Interference graphs: original vs optimized code
- Analysis of how optimization affects register allocation complexity