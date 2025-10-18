# Problem 26: Register Pressure Analysis and Optimization

## Problem Statement
Analyze register pressure patterns and apply code transformations to reduce pressure.

## Three Address Code
```
1:  a = input1
2:  b = input2
3:  c = input3
4:  d = a + b
5:  e = a + c
6:  f = b + c
7:  g = d + e
8:  h = d + f
9:  i = e + f
10: j = g + h + i
11: return j
```

## Task
1. Calculate register pressure at each program point
2. Identify the peak register pressure and its location
3. Apply these pressure-reduction techniques:
   - Instruction scheduling to reduce overlapping live ranges
   - Temporary variable elimination
   - Expression tree reorganization
4. Show how each transformation affects register pressure
5. Perform register allocation on both original and optimized code

## Expected Output Format
- Register pressure graph showing pressure at each program point
- Peak pressure identification and analysis
- Application of each pressure reduction technique
- Comparison of register pressure before/after optimizations
- Register allocation results on optimized code