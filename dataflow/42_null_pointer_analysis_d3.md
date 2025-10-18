# Problem 42: Null Pointer Analysis (Difficulty: d3)

## Problem Statement

Track null pointer states to prevent null pointer dereferences:

```
B1:  p = malloc(10)
     q = null
     goto B2

B2:  if p != null goto B3 else goto B4

B3:  *p = 5      // safe dereference
     q = p       // q becomes non-null
     goto B5

B4:  error()     // p is null
     goto B5

B5:  *q = 10     // safe or unsafe?
     return
```

## Tasks

1. **Define null pointer analysis framework**.

2. **Track pointer states** (null, non-null, unknown).

3. **Identify potential null pointer dereferences**.

## Expected Output Format

- Null state tracking
- Safety analysis
- Error identification