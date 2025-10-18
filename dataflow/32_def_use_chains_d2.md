# Problem 32: Definition-Use Chain Construction (Difficulty: d2)

## Problem Statement

Build definition-use (def-use) chains for the following TAC:

```
B1:  x = 5         // def1 of x
     y = x + 3     // use1 of x, def1 of y
     z = y * 2     // use1 of y, def1 of z
     goto B2

B2:  if x > 4 goto B3 else goto B4  // use2 of x

B3:  x = 10       // def2 of x
     a = x + y    // use3 of x, use2 of y, def1 of a
     goto B5

B4:  y = 20       // def2 of y
     b = x + y    // use4 of x, use3 of y, def1 of b
     goto B5

B5:  c = x + y + z  // use5 of x, use4 of y, use2 of z
     return c
```

## Tasks

1. **Define def-use chain construction** by explaining:
   - What constitutes a definition vs. a use
   - How to connect definitions to their corresponding uses
   - The relationship between reaching definitions and def-use chains

2. **Build def-use chains** for each variable:
   - For each definition, list all uses that it reaches
   - Handle the case where multiple definitions reach the same use

3. **Construct use-def chains** (the reverse):
   - For each use, list all definitions that may reach it

4. **Analyze the results**:
   - Which definitions have no uses (dead code)?
   - Which uses have multiple reaching definitions?
   - How do control flow branches affect the chains?

5. **Applications**: Explain how def-use chains enable:
   - Dead code elimination
   - Register allocation
   - Instruction scheduling

## Expected Output Format

- Definition and use identification for each statement
- Complete def-use chains for all variables
- Use-def chains showing multiple reaching definitions
- Analysis of optimization opportunities revealed by the chains