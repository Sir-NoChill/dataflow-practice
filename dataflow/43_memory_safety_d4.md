# Problem 43: Memory Safety Analysis (Difficulty: d4)

## Problem Statement

Analyze memory safety properties including bounds checking and use-after-free:

```
B1:  ptr = malloc(100)
     index = 0
     goto B2

B2:  if index < 10 goto B3 else goto B5

B3:  ptr[index] = data[index]  // bounds check needed?
     index = index + 1
     goto B2

B4:  // unreachable?
     ptr[50] = 0               // safe access?
     goto B5

B5:  free(ptr)
     goto B6

B6:  result = ptr[0]          // use-after-free?
     return result
```

## Tasks

1. **Define memory safety framework** tracking allocation, bounds, and lifetime.

2. **Apply analysis** to detect safety violations.

3. **Identify all memory safety issues** in the code.

## Expected Output Format

- Memory safety state tracking
- Violation detection
- Safety recommendations