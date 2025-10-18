# Problem 3: Interference Graph with Simple Loop

## Problem Statement
Analyze the following Three Address Code containing a loop and construct its interference graph.

## Three Address Code
```
1:  i = 0
2:  sum = 0
3:  if i >= 10 goto 7
4:  sum = sum + i
5:  i = i + 1
6:  goto 3
7:  return sum
```

## Task
1. Identify the loop structure and draw the control flow graph
2. Perform live variable analysis, paying special attention to variables that are live across loop iterations
3. Construct the interference graph
4. Identify which variables have longer live ranges due to the loop

## Expected Output Format
- Control flow graph showing the loop structure
- Live variable analysis with IN/OUT sets for each basic block
- Interference graph with explanation of loop-induced interferences