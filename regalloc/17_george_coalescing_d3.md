# Problem 17: George's Coalescing Criterion

## Problem Statement
Apply George's coalescing criterion as an alternative to Briggs' approach.

## Three Address Code
```
1:  x = 20
2:  y = 30
3:  z = x + y
4:  a = x          // copy: coalesce x and a?
5:  b = y          // copy: coalesce y and b?
6:  c = z + a
7:  d = b * 2
8:  e = c + d
9:  f = a + b
10: return e + f
```

## Task
1. Construct the interference graph and identify copy operations
2. Apply George's criterion: for copy (u,v), coalesce if for every neighbor t of v, either t interferes with u or has degree < K
3. Compare decisions made by George's criterion vs Briggs' criterion
4. Perform register allocation with the chosen coalescing strategy
5. Analyze the effectiveness of each approach

## Expected Output Format
- Interference graph with copy candidates identified
- Step-by-step application of George's criterion
- Comparison with Briggs' criterion for the same copies
- Register allocation results using each approach
- Analysis of when each criterion performs better