# Problem 13: Loop-Aware Spilling Optimization

## Problem Statement
Optimize spill placement considering loop structure to minimize performance impact.

## Three Address Code
```
1:  i = 0
2:  sum = 0
3:  temp1 = 100
4:  if i >= temp1 goto 10
5:  temp2 = array[i]
6:  temp3 = temp2 * 2
7:  sum = sum + temp3
8:  i = i + 1
9:  goto 4
10: return sum
```

## Task
Assume only 2 registers are available and variable 'temp3' must be spilled:

1. Analyze the loop structure and identify which variables are live across loop iterations
2. Show two spill strategies:
   - Naive: spill/reload temp3 at definition and each use
   - Loop-optimized: minimize spills inside the loop
3. Calculate the expected number of spill operations for each strategy
4. Recommend the better approach and justify your choice

## Expected Output Format
- Loop structure analysis and live variable ranges
- Both spill strategies with modified TAC
- Performance analysis (spill operation counts)
- Recommendation with justification