# Problem 1: Basic Interference Graph Construction

## Problem Statement
Given the following Three Address Code, construct the interference graph for register allocation.

## Three Address Code
```
1:  a = 5
2:  b = a + 3
3:  c = b * 2
4:  d = a + c
5:  return d
```

## Task
1. Perform live variable analysis to determine which variables are live at each program point
2. Construct the interference graph showing which variables cannot share the same register
3. List all edges in your interference graph with justification

## Expected Output Format
- Live variable sets at each program point
- Interference graph as an adjacency list or visual diagram
- Explanation of why each edge exists in the interference graph