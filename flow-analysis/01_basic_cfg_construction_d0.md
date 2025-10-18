# Basic Control Flow Graph Construction

## Problem Statement
Given the following three-address code, construct the control flow graph (CFG). Identify all basic blocks and draw the edges between them.

## Three-Address Code
```
L1: x = a + b
    y = x * 2
    if y > 10 goto L3
L2: z = y - 5
    goto L4
L3: z = y + 3
L4: w = z * z
    return w
```

## Task
1. Identify all basic blocks in the code
2. Draw the control flow graph showing:
   - Basic block boundaries
   - Control flow edges between blocks
   - Entry and exit nodes
3. Label each basic block with a unique identifier

## Expected Output Format
- List of basic blocks with their constituent statements
- Adjacency list or diagram showing control flow edges
- Clear identification of entry and exit blocks