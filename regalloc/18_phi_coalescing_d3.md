# Problem 18: Phi Function Coalescing in SSA

## Problem Statement
Perform coalescing specifically for phi functions during SSA deconstruction.

## Three Address Code (SSA Form)
```
1:  x1 = 10
2:  y1 = 20
3:  if x1 > 5 goto 6
4:  x2 = x1 + 1
5:  goto 7
6:  x3 = x1 - 1
7:  x4 = φ(x2, x3)     // phi function
8:  z1 = x4 * 2
9:  if z1 > 10 goto 12
10: y2 = y1 + x4
11: goto 13
12: y3 = y1 - x4
13: y4 = φ(y2, y3)     // phi function
14: result = x4 + y4
15: return result
```

## Task
1. Identify phi functions and their coalescing opportunities
2. Determine which phi arguments can be coalesced with the phi result
3. Handle cases where phi coalescing conflicts with other interferences
4. Show the parallel copy insertion needed for non-coalesced phi functions
5. Perform final register allocation after phi elimination

## Expected Output Format
- Identification of phi functions and coalescing candidates
- Analysis of interference conflicts for phi coalescing
- Parallel copy insertion for uncoalesced phis
- Final register allocation with phi functions eliminated
- Discussion of critical edge splitting if needed