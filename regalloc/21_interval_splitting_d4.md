# Problem 21: Live Interval Splitting in Linear Scan

## Problem Statement
Apply interval splitting techniques when linear scan allocation encounters register pressure.

## Three Address Code
```
1:  a = input1
2:  b = input2
3:  c = a + b
4:  call_function()  // assume this clobbers registers
5:  d = a + 1
6:  e = b + 1
7:  f = c + d + e
8:  return f
```

## Task
Assume only 2 registers available and function calls require spilling caller-saved registers:

1. Construct live intervals considering function call effects
2. Apply linear scan allocation until register pressure forces a decision
3. Instead of spilling, split a long live interval at an optimal point
4. Show how interval splitting can reduce register pressure
5. Complete allocation with the split intervals

## Expected Output Format
- Live intervals with function call boundaries marked
- Linear scan execution until splitting decision point
- Interval splitting analysis and optimal split point selection
- Allocation completion with split intervals
- Performance comparison: splitting vs spilling