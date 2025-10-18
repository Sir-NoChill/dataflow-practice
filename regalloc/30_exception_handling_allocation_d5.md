# Problem 30: Register Allocation with Exception Handling

## Problem Statement
Handle register allocation in the presence of exception handling constructs and unwind requirements.

## Three Address Code
```
1:  a = 10
2:  b = 20
3:  try_begin:
4:    c = risky_operation(a)    // may throw exception
5:    d = c + b
6:    e = process(d)           // may throw exception
7:    f = e * 2
8:  try_end:
9:    return f
10: catch_begin:
11:   error_val = get_exception()
12:   cleanup_a = a            // 'a' must be available for cleanup
13:   result = handle_error(error_val, cleanup_a)
14:   return result
15: catch_end:
```

## Task
1. Identify variables that must remain live across exception boundaries
2. Modify live variable analysis to account for exception control flow
3. Ensure critical variables are in callee-saved registers or memory
4. Handle register allocation for exception handling code
5. Optimize for both normal and exceptional control flow paths

## Expected Output Format
- Exception control flow graph with all possible paths
- Modified live variable analysis including exception edges
- Identification of exception-live variables
- Register allocation strategy for exception safety
- Performance analysis of exception handling overhead