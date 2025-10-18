# Problem 40: Debugging Register Allocation Failures

## Problem Statement
Diagnose and fix a failing register allocation scenario with systematic debugging techniques.

## Three Address Code (problematic allocation)
```
1:  a = input1
2:  b = input2
3:  c = a + b
4:  d = a * b
5:  e = c + d
6:  f = a + c + d + e
7:  g = b + c + d + e
8:  h = f * g
9:  return h
```

## Given Failed Allocation Attempt
- 3 registers available: R1, R2, R3
- Previous attempt resulted in excessive spilling
- Suspicion that the allocation algorithm made suboptimal decisions

## Task
1. Reconstruct the interference graph and identify the allocation challenge
2. Apply systematic debugging:
   - Check for errors in live variable analysis
   - Verify interference graph construction
   - Analyze spill candidate selection decisions
3. Identify the root cause of allocation failure
4. Propose and implement a fix (algorithm modification or code transformation)
5. Verify the improved allocation

## Expected Output Format
- Systematic debugging process documentation
- Root cause analysis of allocation failure
- Proposed solution with justification
- Verification of improved allocation
- General debugging guidelines for allocation problems