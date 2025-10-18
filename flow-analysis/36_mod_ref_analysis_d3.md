# Mod-Ref Analysis

## Problem Statement
Perform modification-reference analysis to determine which memory locations functions may modify or reference.

## Three-Address Code
```
function main():
B1: global_array[0] = 10
    local_var = 20
    ptr = &local_var
    call function_A(global_array, ptr)
    result = global_array[0] + local_var
    return result

function function_A(arr, p):
B2: temp = arr[0]              // reference to arr[0]
    *p = temp + 5              // modify *p
    call function_B(arr + 1)
    arr[1] = *p                // modify arr[1], reference *p
    return

function function_B(sub_arr):
B3: if condition goto B4
    goto B5
B4: sub_arr[0] = 100          // modify sub_arr[0]
    call external_func()       // unknown effects
    return
B5: value = sub_arr[0]        // reference sub_arr[0]
    return value
```

## Tasks
1. Compute Mod and Ref sets for each function
2. Handle pointer parameters and aliasing effects
3. Analyze transitive effects through function calls
4. Account for unknown external function effects
5. Use Mod-Ref information for optimization decisions

## Expected Output Format
- Mod and Ref sets for each function
- Parameter aliasing analysis
- Transitive effect computation through call chain
- Summary of optimization opportunities enabled by Mod-Ref analysis
- Comparison with conservative assumptions