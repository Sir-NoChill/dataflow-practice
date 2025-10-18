# Problem 2: Live Variable Analysis with Conditional Branches

## Problem Statement
Perform live variable analysis on the following Three Address Code that contains conditional branches.

## Three Address Code
```
1:  x = 10
2:  y = 20
3:  if x > 5 goto 6
4:  z = x + y
5:  goto 7
6:  z = x - y
7:  w = z * 2
8:  return w
```

## Task
1. Draw the control flow graph (CFG) for this code
2. Perform live variable analysis using the dataflow equations:
   - OUT[n] = ∪(s∈succ[n]) IN[s]
   - IN[n] = use[n] ∪ (OUT[n] - def[n])
3. Show the IN and OUT sets for each basic block
4. Construct the interference graph based on your live variable analysis

## Expected Output Format
- Control flow graph with basic blocks clearly labeled
- Iteration-by-iteration computation of IN/OUT sets until fixed point
- Final interference graph