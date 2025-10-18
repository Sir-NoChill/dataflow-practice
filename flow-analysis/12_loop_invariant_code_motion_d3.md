# Loop Invariant Code Motion Analysis

## Problem Statement
Analyze the following code for loop invariant expressions and determine safe code motion opportunities.

## Three-Address Code
```
B1: base = &array[0]
    limit = n * sizeof(int)
    offset = start * sizeof(int)
    goto B2
B2: if offset >= limit goto B8
B3: addr1 = base + offset
    temp1 = *addr1
    factor = multiplier * 2
    goto B4
B4: if temp1 <= 0 goto B7
B5: temp2 = temp1 * factor
    result = temp2 + constant
    addr2 = base + offset
    *addr2 = result
    goto B6
B6: offset = offset + sizeof(int)
    counter = counter + 1
    goto B7
B7: log_addr = &log_array[0]
    entry = log_addr + counter * 8
    *entry = temp1
    goto B2
B8: return
```

## Tasks
1. Identify the loop structure and loop-invariant expressions
2. Determine which expressions are safe to move out of the loop
3. Check for aliasing and side-effect constraints
4. Analyze dominance requirements for code motion
5. Propose the transformed code with expressions moved to preheader

## Expected Output Format
- Loop boundary identification
- List of loop-invariant expressions with safety analysis
- Aliasing and side-effect analysis
- Dominance constraints for each candidate expression
- Transformed code showing expressions moved to appropriate locations