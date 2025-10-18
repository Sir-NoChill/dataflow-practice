# Problem 45: Escape Analysis (Difficulty: d4)

## Problem Statement

Determine which objects escape their allocation scope:

```
function create_local():
B1:  local_obj = new Object()
     local_obj.field = 42
     return local_obj          // escapes via return

function process_data():
B2:  obj1 = new Object()      // local only?
     obj2 = new Object()
     global_ptr = obj2         // escapes via global
     temp = obj1.field + obj2.field
     return temp               // obj1 escapes?
```

## Tasks

1. **Define escape analysis framework**.

2. **Track object escape paths** (return, globals, parameters).

3. **Identify stack allocation opportunities**.

## Expected Output Format

- Escape analysis results
- Stack vs. heap allocation decisions
- Optimization opportunities