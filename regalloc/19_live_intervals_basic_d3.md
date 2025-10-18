# Problem 19: Live Interval Construction for Linear Scan

## Problem Statement
Construct live intervals for linear scan register allocation from the given Three Address Code.

## Three Address Code
```
1:  a = 10
2:  b = 20
3:  c = a + b
4:  d = a * 2
5:  e = b + c
6:  f = d + e
7:  return f
```

## Task
1. Number each instruction with program points (before and after each instruction)
2. Perform live variable analysis to determine variable lifetimes
3. Construct live intervals for each variable showing [start, end) ranges
4. Sort intervals by start point for linear scan processing
5. Identify any holes in live intervals and explain their significance

## Expected Output Format
- Program points numbered for each instruction position
- Live variable analysis showing live sets at each program point
- Live intervals for each variable with precise start/end points
- Sorted list of intervals by start point
- Analysis of interval properties (length, overlaps, holes)