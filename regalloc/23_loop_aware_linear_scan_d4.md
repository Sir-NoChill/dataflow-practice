# Problem 23: Loop-Aware Linear Scan Allocation

## Problem Statement
Modify linear scan allocation to be aware of loop structures and optimize for loop performance.

## Three Address Code
```
1:  i = 0
2:  sum = 0
3:  if i >= 100 goto 8
4:  temp = array[i]
5:  sum = sum + temp
6:  i = i + 1
7:  goto 3
8:  return sum
```

## Task
1. Identify the loop structure and variables live across loop iterations
2. Construct live intervals considering loop back-edges
3. Apply loop-aware priorities in linear scan (prefer keeping loop variables in registers)
4. Show how loop-aware allocation differs from basic linear scan
5. Analyze the performance benefits for loop-intensive code

## Expected Output Format
- Loop structure analysis and back-edge identification
- Live intervals with loop-carried dependencies marked
- Linear scan allocation with loop-aware priorities
- Comparison with basic linear scan results
- Performance analysis for loop execution