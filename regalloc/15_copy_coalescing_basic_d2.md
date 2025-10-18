# Problem 15: Basic Copy Coalescing

## Problem Statement
Identify and perform copy coalescing opportunities to reduce register pressure and eliminate move instructions.

## Three Address Code
```
1:  a = 10
2:  b = a          // copy
3:  c = b + 5
4:  d = c
5:  e = d * 2      // copy
6:  f = a + e
7:  return f
```

## Task
1. Identify all copy operations in the code
2. Determine which copies can be safely coalesced (variables can share the same register)
3. Apply coalescing and show the simplified interference graph
4. Perform register allocation on the coalesced graph
5. Show the final code with moves eliminated

## Expected Output Format
- Identification of copy operations
- Interference graph before coalescing
- Coalescing analysis (which copies are safe to coalesce)
- Modified interference graph after coalescing
- Final register allocation and optimized code