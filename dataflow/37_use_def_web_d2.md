# Problem 37: Use-Def Web Construction (Difficulty: d2)

## Problem Statement

Construct use-def webs (also called variable webs) for register allocation:

```
B1:  a = 5
     b = a + 3    // use of a
     goto B2

B2:  if b > 6 goto B3 else goto B4

B3:  a = 10      // new definition of a
     c = a + b   // use of new a
     goto B5

B4:  c = a + 1   // use of original a
     goto B5

B5:  d = a + c   // which a is used?
     return d
```

## Tasks

1. **Define use-def webs**: How do webs differ from simple def-use chains?

2. **Construct separate webs** for each variable showing connected components of definitions and uses.

3. **Analyze web properties**:
   - Which variables have multiple webs?
   - How do control flow merges affect web construction?

4. **Apply to register allocation**: Show how webs can be assigned to different registers.

## Expected Output Format

- Web construction for each variable
- Register assignment based on webs
- Analysis of register requirements