# Problem 31: Register Renaming and False Dependencies

## Problem Statement
Apply register renaming to eliminate false dependencies and improve register allocation.

## Three Address Code (with false dependencies)
```
1:  a = 10
2:  b = a + 5      // true dependency on a
3:  a = 20         // redefines a, creating false dependency
4:  c = a + 3      // uses new value of a
5:  d = b * 2      // uses old value computation
6:  e = c + d
7:  return e
```

## Task
1. Identify true vs false dependencies in the original code
2. Apply register renaming to eliminate false dependencies
3. Construct interference graphs before and after renaming
4. Perform register allocation on both versions
5. Analyze the impact of renaming on register pressure and allocation quality

## Expected Output Format
- Dependency analysis (true vs false dependencies)
- Register renaming transformation
- Interference graphs before and after renaming
- Register allocation comparison
- Analysis of renaming benefits for allocation