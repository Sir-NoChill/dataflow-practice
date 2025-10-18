# CFG Construction with Switch and Fall-through

## Problem Statement
Construct the control flow graph for the following three-address code representing a switch statement with fall-through cases.

## Three-Address Code
```
    t1 = input
    if t1 == 1 goto L_case1
    if t1 == 2 goto L_case2
    if t1 == 3 goto L_case3
    goto L_default
L_case1:
    result = 100
    // fall through to case 2
L_case2:
    result = result + 50
    if flag goto L_exit
    // fall through to case 3
L_case3:
    result = result * 2
    goto L_exit
L_default:
    result = 0
L_exit:
    return result
```

## Tasks
1. Identify all basic blocks, paying attention to fall-through behavior
2. Construct the CFG showing:
   - Switch dispatch logic
   - Fall-through paths between cases
   - Conditional exit from fall-through
3. Identify any unreachable code

## Expected Output Format
- Basic block list with fall-through considerations
- CFG diagram with all possible execution paths
- Analysis of reachability for each block