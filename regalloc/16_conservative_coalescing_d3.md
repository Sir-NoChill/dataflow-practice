# Problem 16: Conservative Coalescing with Briggs' Criterion

## Problem Statement
Apply conservative coalescing using Briggs' criterion to avoid increasing spill potential.

## Three Address Code
```
1:  a = input1
2:  b = input2
3:  c = a + b
4:  d = a          // copy candidate
5:  e = b          // copy candidate
6:  f = c + d
7:  g = c + e
8:  h = f * g
9:  return h
```

## Task
1. Construct the initial interference graph
2. Identify copy operations that are candidates for coalescing
3. Apply Briggs' criterion: coalesce only if the merged node has fewer than K neighbors with degree ≥ K
4. Show which coalescing operations are safe and which are rejected
5. Perform register allocation with K=3 registers

## Expected Output Format
- Initial interference graph with copy operations marked
- Application of Briggs' criterion for each copy candidate
- Decisions on which copies to coalesce and rationale
- Final register allocation after conservative coalescing
- Analysis of how conservative coalescing prevents spilling