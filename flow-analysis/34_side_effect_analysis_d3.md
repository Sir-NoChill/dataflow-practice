# Side Effect Analysis

## Problem Statement
Analyze side effects to enable aggressive optimization while preserving program semantics.

## Three-Address Code
```
B1: global_var = 0
    call init_system()
    goto B2
B2: local_result = pure_function(x, y)
    temp = call may_have_effects(z)
    global_var = global_var + 1
    goto B3
B3: if condition goto B4
    goto B5
B4: call log_message(temp)         // I/O side effect
    cache[key] = local_result      // memory side effect
    goto B6
B5: volatile_read = *volatile_ptr   // volatile side effect
    call external_lib(volatile_read) // unknown side effects
    goto B6
B6: final_result = pure_function(temp, local_result)
    if global_var > 10 goto B7
    goto B2
B7: return final_result
```

## Tasks
1. Classify operations by their side effect types (memory, I/O, control, etc.)
2. Analyze side effect dependencies and ordering constraints
3. Identify pure computations that can be optimized aggressively
4. Determine safe code motion considering side effects
5. Model the interaction between side effects and other optimizations

## Expected Output Format
- Side effect classification for each operation
- Dependency analysis considering side effects
- Pure vs impure operation identification
- Code motion safety analysis
- Optimization constraints imposed by side effects