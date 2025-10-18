# Problem 39: Global Value Numbering (Difficulty: d3)

## Problem Statement

Apply global value numbering for redundancy elimination:

```
B1:  a = x + y
     b = x + y    // redundant?
     goto B2

B2:  if a > 10 goto B3 else goto B4

B3:  c = x + y   // redundant with a?
     d = c * 2
     goto B5

B4:  e = x + y   // redundant with a?
     f = e + 1
     goto B5

B5:  g = x + y   // available from which path?
     return g
```

## Tasks

1. **Define global value numbering framework**.

2. **Apply value numbering** to identify equivalent expressions across basic blocks.

3. **Show optimized code** with redundancy elimination.

## Expected Output Format

- Value numbering assignment
- Redundancy elimination results
- Optimized code