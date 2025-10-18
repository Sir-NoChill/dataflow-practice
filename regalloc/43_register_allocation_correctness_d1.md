# Problem 43: Verifying Register Allocation Correctness

## Problem Statement
Verify the correctness of a given register allocation and identify any semantic errors.

## Three Address Code
```
1:  a = 10
2:  b = 20
3:  c = a + b
4:  if c > 25 goto 7
5:  d = a * 2
6:  goto 8
7:  d = b + 5
8:  e = d + c
9:  return e
```

## Given Register Allocation
- a → R1 (lines 1-5)
- b → R2 (lines 2-7)
- c → R1 (lines 3-8) // POTENTIAL CONFLICT!
- d → R2 (lines 5-8, 7-8)
- e → R1 (line 8-9)

## Task
1. Trace through the execution paths and verify register assignments
2. Check for any register conflicts where the same register holds different live variables
3. Verify that variable values are preserved correctly across their live ranges
4. Identify any correctness violations and their root causes
5. Propose corrections to fix any identified problems

## Expected Output Format
- Step-by-step execution trace for all possible paths
- Identification of register conflicts or correctness violations
- Root cause analysis of any problems found
- Corrected register allocation ensuring correctness
- Verification methodology for checking allocation correctness