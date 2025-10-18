# Problem 10: Register Allocation with Precolored Registers

## Problem Statement
Perform register allocation when some variables are precolored due to calling conventions.

## Three Address Code (Function with specific calling convention)
```
// Function parameters arrive in R1, R2
// Return value must be in R1
1:  param1 = R1   // a arrives in R1
2:  param2 = R2   // b arrives in R2
3:  temp1 = param1 + param2
4:  temp2 = param1 * 2
5:  temp3 = param2 * 3
6:  result = temp1 + temp2 + temp3
7:  R1 = result   // return value must be in R1
8:  return
```

## Task
1. Identify precolored variables (those constrained to specific registers)
2. Perform live variable analysis considering precolored constraints
3. Construct interference graph including precolored nodes
4. Perform graph coloring with 4 total registers (R1, R2, R3, R4) where R1 and R2 have precoloring constraints
5. Handle conflicts between precolored registers and temporary variables

## Expected Output Format
- Identification of precolored variables and their constraints
- Modified interference graph showing precolored nodes
- Step-by-step register allocation handling precolored constraints
- Final register assignment respecting calling conventions