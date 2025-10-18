# Problem 9: Register Allocation with Multiple Register Classes

## Problem Statement
Perform register allocation considering both integer and floating-point register classes.

## Three Address Code
```
1:  x = 10        // integer
2:  y = 3.14      // float
3:  z = 2.71      // float
4:  a = x + 5     // integer
5:  b = y * z     // float
6:  c = x * 2     // integer
7:  d = b + y     // float
8:  if a > c goto 11
9:  e = d / z     // float
10: goto 12
11: e = y - b     // float
12: return e
```

## Task
1. Classify each variable by its register class (integer vs floating-point)
2. Perform live variable analysis
3. Construct separate interference graphs for each register class
4. Perform register allocation assuming 2 integer registers (R1, R2) and 2 floating-point registers (F1, F2)
5. Identify any cross-class register pressure issues

## Expected Output Format
- Variable classification by register class
- Separate interference graphs for integer and floating-point variables
- Register allocation for each class
- Analysis of register pressure per class