# Problem 24: Register Allocation with Calling Convention Constraints

## Problem Statement
Handle register allocation across function calls with complex calling convention requirements.

## Three Address Code
```
// Function: compute(int a, int b, int c)
// Calling convention: params in R1, R2, R3; return in R1; R4-R6 caller-saved; R7-R8 callee-saved
1:  param_a = R1      // parameter a
2:  param_b = R2      // parameter b
3:  param_c = R3      // parameter c
4:  temp1 = param_a + param_b
5:  temp2 = param_c * 2
6:  // call helper(temp1, temp2) - clobbers R1-R6
7:  R1 = temp1        // setup call
8:  R2 = temp2        // setup call
9:  call helper
10: result1 = R1      // get return value
11: temp3 = param_c + result1
12: temp4 = param_a * result1
13: final = temp3 + temp4
14: R1 = final        // setup return
15: return
```

## Task
1. Identify all calling convention constraints (parameter passing, return values, register preservation)
2. Perform register allocation considering function call boundaries
3. Handle caller-saved register spilling around the function call
4. Optimize register usage for callee-saved registers
5. Show the complete allocation including call setup and cleanup

## Expected Output Format
- Analysis of calling convention constraints
- Live variable analysis across function call boundaries
- Register allocation strategy for caller/callee-saved registers
- Spill/restore code insertion around function calls
- Final optimized allocation respecting all constraints