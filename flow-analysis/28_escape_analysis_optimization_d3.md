# Escape Analysis for Optimization

## Problem Statement
Perform escape analysis to identify optimization opportunities for heap allocation and synchronization.

## Three-Address Code
```
function processData(global_flag):
B1: local_obj = new Object()
    local_obj.field1 = input
    local_obj.field2 = compute(input)
    temp_array = new Array[10]
    goto B2
B2: for i = 0 to 9
B3:   temp_array[i] = local_obj.field1 * i
      if global_flag goto B4
      goto B5
B4:   global_ptr = local_obj     // potential escape
      global_array = temp_array   // potential escape
      goto B5
B5: end for
    result = temp_array[5]
    if result > threshold goto B6
    goto B7
B6: return local_obj            // escape through return
B7: return result               // no escape
```

## Tasks
1. Track object allocation sites and their usage patterns
2. Determine which objects escape their allocation scope
3. Identify objects that can be stack-allocated instead of heap-allocated
4. Analyze escape through parameters, returns, and global assignments
5. Propose optimizations based on escape analysis results

## Expected Output Format
- Escape analysis for each allocation site
- Classification of objects (local, parameter escape, global escape, return escape)
- Stack allocation optimization opportunities
- Synchronization elimination possibilities
- Memory management optimization recommendations