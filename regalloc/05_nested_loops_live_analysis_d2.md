# Problem 5: Live Variable Analysis in Nested Loops

## Problem Statement
Analyze the live variables in the following Three Address Code with nested loops.

## Three Address Code
```
1:  n = 100
2:  i = 0
3:  result = 0
4:  if i >= n goto 13
5:  j = 0
6:  temp = 0
7:  if j >= i goto 11
8:  temp = temp + j
9:  j = j + 1
10: goto 7
11: result = result + temp
12: i = i + 1
13: goto 4
14: return result
```

## Task
1. Draw the control flow graph showing the nested loop structure
2. Perform live variable analysis, showing how variables are live across multiple loop levels
3. Identify variables that are live across the outer loop, inner loop, or both
4. Construct the interference graph and explain how nested loops affect register pressure

## Expected Output Format
- Control flow graph with nested loop structure clearly marked
- Live variable analysis with careful attention to loop boundaries
- Classification of variables by their live ranges relative to loop nesting
- Interference graph with analysis of register pressure