# Problem 8: Graph Coloring with Node Selection Heuristics

## Problem Statement
Apply graph coloring register allocation using different node selection heuristics and compare results.

## Three Address Code
```
1:  a = input1
2:  b = input2
3:  c = a + b
4:  d = a * 2
5:  e = b * 3
6:  f = c + d
7:  g = d + e
8:  h = f * g
9:  return h
```

## Task
1. Perform live variable analysis and construct the interference graph
2. Apply graph coloring with 4 registers using these heuristics:
   - Lowest degree first
   - Highest degree first
   - Most constrained first (degree/remaining colors)
3. Compare the success/failure of each heuristic
4. Analyze which heuristic performs better and why

## Expected Output Format
- Live variable analysis and interference graph
- Step-by-step application of each heuristic
- Comparison table showing results of each approach
- Analysis of heuristic effectiveness