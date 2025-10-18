# Problem 27: Comprehensive Algorithm Comparison

## Problem Statement
Compare graph coloring, linear scan, and a hybrid approach on the same register allocation problem.

## Three Address Code
```
1:  x = 5
2:  y = 10
3:  if x > 0 goto 6
4:  z = y * 2
5:  goto 8
6:  z = y + x
7:  w = z * x
8:  a = z + y
9:  for i = 0 to 3
10:   b = a + i
11:   a = b * 2
12: end for
13: return a
```

## Task
Apply all three approaches with 3 available registers:

1. **Graph Coloring**: Construct interference graph, apply coloring with spilling if needed
2. **Linear Scan**: Build live intervals, apply linear scan allocation
3. **Hybrid**: Use linear scan for straight-line code, graph coloring for complex control flow

For each approach:
- Show the complete allocation process
- Count spill operations required
- Analyze code quality and compilation time trade-offs

## Expected Output Format
- Complete analysis for each algorithm approach
- Spill operation counts and code quality metrics
- Compilation complexity analysis (time/space)
- Recommendation for different code patterns
- Discussion of when each algorithm performs best