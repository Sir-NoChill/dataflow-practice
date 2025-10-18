# Problem 11: Spill Candidate Selection Heuristics

## Problem Statement
When register allocation fails, select appropriate spill candidates using different heuristics.

## Three Address Code
```
1:  a = input1
2:  b = input2
3:  c = a + 1
4:  d = b + 1
5:  e = c * d
6:  f = a + b
7:  g = e + f
8:  h = c + d
9:  i = g * h
10: j = e + f + g + h
11: return j
```

## Task
1. Perform live variable analysis and construct interference graph
2. Attempt graph coloring with only 2 registers
3. When coloring fails, apply these spill candidate selection heuristics:
   - Lowest use count
   - Longest live range
   - Lowest degree in interference graph
   - Cost-benefit analysis (use count / spill cost)
4. For each heuristic, show which variable would be selected for spilling
5. Analyze the trade-offs of each approach

## Expected Output Format
- Interference graph and failed coloring attempt
- Application of each spill selection heuristic with justification
- Comparison table of spill candidates selected by each method
- Analysis of expected performance impact for each choice