# Memory Disambiguation Analysis

## Problem Statement
Perform memory disambiguation to enable aggressive optimization in the presence of pointer accesses.

## Three-Address Code
```
B1: p = &array[0]
    q = &array[100]
    r = &local_var
    base = malloc(1000)
    s = base + offset
    goto B2
B2: for i = 0 to n-1
B3:   *p = expr1(i)              // Store 1
      temp1 = *q                 // Load 1
      *s = expr2(temp1)          // Store 2
      temp2 = *r                 // Load 2
      *p = temp2 + 10            // Store 3
      result = *q + *s           // Load 3, Load 4
      p = p + 1
      s = s + 4
B4: end for
    return result
```

## Tasks
1. Analyze pointer arithmetic and base address relationships
2. Determine which memory accesses may alias
3. Identify disambiguation opportunities for load/store optimization
4. Apply memory disambiguation to enable code motion
5. Analyze the effect on available expressions and CSE

## Expected Output Format
- Alias analysis results for all pointer dereferences
- Memory access classification (must-alias, may-alias, no-alias)
- Load/store optimization opportunities
- Code motion possibilities enabled by disambiguation
- Impact on other dataflow analyses