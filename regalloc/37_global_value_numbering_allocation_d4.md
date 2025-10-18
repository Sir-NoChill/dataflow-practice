# Problem 37: Register Allocation with Global Value Numbering

## Problem Statement
Perform register allocation after global value numbering optimization, handling the interaction between optimization and allocation.

## Three Address Code (before GVN)
```
1:  a = x + y
2:  b = 2
3:  c = a * b
4:  if condition goto 7
5:  d = x + y      // redundant computation
6:  goto 8
7:  d = a          // equivalent to x + y
8:  e = d * 2      // equivalent to d * b
9:  f = c + e
10: return f
```

## Task
1. Apply global value numbering to eliminate redundant computations
2. Show how GVN affects variable lifetimes and live ranges
3. Identify new coalescing opportunities created by GVN
4. Perform register allocation on the GVN-optimized code
5. Compare register allocation quality before and after GVN

## Expected Output Format
- Global value numbering analysis and optimization
- Modified TAC after GVN optimization
- Impact analysis on live variable ranges
- Register allocation on optimized code
- Comparison of allocation quality and register pressure