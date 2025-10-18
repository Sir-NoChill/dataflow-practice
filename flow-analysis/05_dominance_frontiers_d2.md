# Dominance Frontiers Computation

## Problem Statement
Given the following three-address code, construct the CFG and compute dominance frontiers for SSA form construction.

## Three-Address Code
```
Entry:
    goto B1
B1: x = 5
    y = 10
    if condition goto B3
B2: x = x + 1
    goto B5
B3: if condition2 goto B4
    goto B5
B4: y = y * 2
    x = y + 3
    goto B5
B5: z = x + y
    if z > 20 goto B6
    goto B7
B6: result = z * 2
    goto B8
B7: result = z + 5
B8: return result
```

## Tasks
1. Construct the control flow graph
2. Compute dominance sets and immediate dominators
3. Calculate dominance frontiers DF(n) for each node n
4. Identify where φ-functions would be needed for variables x, y, z

## Expected Output Format
- CFG representation
- Dominance tree
- DF(n) for each node n
- φ-function placement analysis for each variable