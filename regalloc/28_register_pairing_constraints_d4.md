# Problem 28: Register Pairing and Alignment Constraints

## Problem Statement
Handle register allocation with architectural constraints requiring register pairs for certain operations.

## Three Address Code
```
1:  a = 100           // 32-bit integer
2:  b = 200           // 32-bit integer
3:  long1 = extend(a) // 64-bit requires register pair
4:  long2 = extend(b) // 64-bit requires register pair
5:  long3 = long1 + long2  // 64-bit addition
6:  c = truncate(long3)    // back to 32-bit
7:  d = a + b         // 32-bit operation
8:  return c + d
```

## Architecture Constraints
- 32-bit values use single registers: R1, R2, R3, R4
- 64-bit values require aligned register pairs: (R1,R2) or (R3,R4)
- Mixed operations may require temporary pairs

## Task
1. Classify variables by their register requirements (single vs pair)
2. Modify interference graph construction for pairing constraints
3. Apply register allocation respecting alignment requirements
4. Handle spilling of register pairs
5. Optimize for minimal pair fragmentation

## Expected Output Format
- Variable classification by register width requirements
- Modified interference graph with pairing constraints
- Register allocation algorithm handling pairs
- Spilling strategy for paired registers
- Analysis of register utilization efficiency