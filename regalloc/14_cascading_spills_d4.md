# Problem 14: Cascading Spills and Iterative Allocation

## Problem Statement
Handle the cascading effects when spill code insertion creates new register pressure.

## Three Address Code
```
1:  a = input1
2:  b = input2
3:  c = input3
4:  d = a + b
5:  e = b + c
6:  f = c + a
7:  g = d + e + f
8:  return g
```

## Task
Assume only 2 registers available:

1. Perform initial register allocation attempt and identify first spill candidate
2. Insert spill code for the first candidate
3. Reanalyze register allocation - identify if cascading spills are needed
4. Continue iteratively until a valid allocation is found
5. Show how spill temporaries can create additional register pressure

## Expected Output Format
- Initial allocation attempt and first spill decision
- Step-by-step iteration showing each spill insertion
- Analysis of how each spill affects subsequent allocation
- Final allocation with all necessary spill code
- Discussion of algorithm termination guarantees