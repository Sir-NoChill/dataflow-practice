# Partial Redundancy Elimination

## Problem Statement
Implement partial redundancy elimination using the lazy code motion framework.

## Three-Address Code
```
B1: a = input
    b = input2
    goto B2
B2: if a > 0 goto B3
    goto B6
B3: x = a + b              // expression computed
    if x > 10 goto B4
    goto B5
B4: y = x * 2
    z = a + b              // fully redundant
    goto B5
B5: w = a + b              // partially redundant (available from B3)
    goto B7
B6: if b < 0 goto B7
    x = a + b              // expression computed on this path
    goto B7
B7: result = a + b         // partially redundant (available from B3, B6)
    return result
```

## Tasks
1. Compute anticipable expressions (ANTLOC, ANTIN)
2. Calculate available expressions (AVLOC, AVIN)
3. Determine earliest and latest computation points
4. Apply lazy code motion to eliminate partial redundancies
5. Generate optimized code with minimal expression evaluations

## Expected Output Format
- ANTLOC, ANTIN, AVLOC, AVIN analysis results
- Earliest and latest computation point analysis
- Code motion decisions for each expression
- Optimized code with inserted and deleted computations
- Verification that partial redundancies are eliminated