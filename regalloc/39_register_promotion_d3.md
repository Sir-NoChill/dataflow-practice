# Problem 39: Register Promotion from Memory

## Problem Statement
Identify memory-based variables that can be promoted to registers and integrate this with register allocation.

## Three Address Code
```
1:  store 10, var_a        // var_a initially in memory
2:  store 20, var_b        // var_b initially in memory
3:  for i = 0 to 100:
4:    temp1 = load var_a
5:    temp2 = load var_b
6:    temp3 = temp1 + temp2
7:    store temp3, var_a
8:    temp4 = temp2 * 2
9:    store temp4, var_b
10: end for
11: result_a = load var_a
12: result_b = load var_b
13: return result_a + result_b
```

## Task
1. Identify memory variables that are candidates for register promotion
2. Analyze the benefits of promoting each variable (load/store elimination)
3. Promote suitable variables and modify the code
4. Perform register allocation including the promoted variables
5. Handle spilling of promoted variables back to their original memory locations

## Expected Output Format
- Register promotion candidate analysis
- Cost-benefit analysis for each promotion
- Code transformation after promotion
- Register allocation including promoted variables
- Spilling strategy back to original memory locations