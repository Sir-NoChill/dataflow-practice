# Problem 25: Interprocedural Register Allocation

## Problem Statement
Perform register allocation across multiple function boundaries with optimization opportunities.

## Three Address Code (Two Functions)
```
// Function: helper(int x, int y)
1:  param_x = R1
2:  param_y = R2
3:  temp = param_x + param_y
4:  result = temp * 2
5:  R1 = result
6:  return

// Function: main()
7:  a = 10
8:  b = 20
9:  c = 30
10: // call helper(a, b)
11: R1 = a
12: R2 = b
13: call helper
14: temp1 = R1
15: d = temp1 + c
16: // call helper(c, d)
17: R1 = c
18: R2 = d
19: call helper
20: temp2 = R1
21: return temp2
```

## Task
1. Analyze register usage patterns across both functions
2. Identify opportunities for interprocedural optimization
3. Propose a custom calling convention that would improve register allocation
4. Show how global register allocation could eliminate redundant moves
5. Compare costs: standard calling convention vs optimized interprocedural allocation

## Expected Output Format
- Register usage analysis for each function
- Identification of interprocedural optimization opportunities
- Proposed custom calling convention with justification
- Global allocation strategy across function boundaries
- Cost-benefit analysis of interprocedural vs intraprocedural allocation