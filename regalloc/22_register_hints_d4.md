# Problem 22: Register Hints and Copy Optimization in Linear Scan

## Problem Statement
Use register hints in linear scan allocation to minimize move instructions.

## Three Address Code
```
1:  a = 10
2:  b = a          // hint: prefer same register as 'a'
3:  c = 20
4:  d = c          // hint: prefer same register as 'c'
5:  e = b + d
6:  f = a + c      // 'a' and 'c' might still be needed
7:  return e + f
```

## Task
1. Construct live intervals and identify copy relationships
2. Determine register hints based on copy operations
3. Apply linear scan allocation incorporating register hints
4. Show how hints influence register assignment decisions
5. Count move instructions eliminated through hint-guided allocation

## Expected Output Format
- Live intervals with copy relationships identified
- Register hint analysis for each variable
- Linear scan execution showing hint influence on decisions
- Final allocation with move elimination count
- Analysis of hint effectiveness in reducing code size