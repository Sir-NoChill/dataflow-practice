# Problem 12: Spill Code Insertion and Register Pressure

## Problem Statement
Insert spill code for a selected variable and analyze the impact on register allocation.

## Three Address Code
```
1:  a = 10
2:  b = 20
3:  c = a + b
4:  d = a * b
5:  e = c + d
6:  f = a + c
7:  g = d + e
8:  return g
```

## Task
Assume variable 'e' must be spilled due to register pressure:

1. Insert spill code (store and reload instructions) for variable 'e'
2. Recompute live variable analysis for the modified code
3. Construct the new interference graph after spill code insertion
4. Analyze how spilling 'e' affects the register allocation of other variables
5. Determine if additional spilling might be needed

## Expected Output Format
- Original interference graph showing why spilling is needed
- Modified TAC with spill/reload instructions inserted
- New live variable analysis after spill code insertion
- New interference graph and register allocation
- Analysis of cascading effects from spilling