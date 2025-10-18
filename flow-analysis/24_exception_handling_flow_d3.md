# Exception Handling Control Flow

## Problem Statement
Analyze control flow and dataflow in the presence of exception handling constructs.

## Three-Address Code
```
B1: try_begin
    x = risky_operation(a)
    y = x + 10
    z = another_risky_op(y)
    try_end
    goto B5
B2: catch_begin(Exception1)
    x = default_value1
    log_error("Exception1")
    goto B4
B3: catch_begin(Exception2)
    x = default_value2
    y = x * 2
    log_error("Exception2")
    goto B4
B4: catch_end
    result = x + y
    goto B6
B5: normal_path:
    result = z + x + y
    goto B6
B6: finally_begin
    cleanup()
    finally_end
    return result
```

## Tasks
1. Model exception control flow edges in the CFG
2. Analyze how exceptions affect dominance relationships
3. Determine live variables considering exception paths
4. Handle dataflow analysis with exceptional control flow
5. Identify optimization constraints due to exception semantics

## Expected Output Format
- CFG with exceptional control flow edges
- Modified dominance analysis considering exception paths
- Live variable analysis with exception handling
- Dataflow constraints imposed by exception semantics
- Optimization opportunities and limitations