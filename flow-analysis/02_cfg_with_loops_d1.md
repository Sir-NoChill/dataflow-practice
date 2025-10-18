# CFG Construction with Loop Structures

## Problem Statement
Convert the following C-like code to three-address code, then construct the control flow graph.

## Source Code
```c
int sum = 0;
for (int i = 0; i < n; i++) {
    if (arr[i] > threshold) {
        sum += arr[i];
    } else {
        continue;
    }
    count++;
}
return sum;
```

## Tasks
1. Convert the source code to three-address code
2. Identify all basic blocks
3. Construct the CFG showing:
   - Loop structure
   - Continue statement handling
   - Conditional branches within the loop

## Expected Output Format
- Three-address code representation
- Basic block identification
- CFG with clearly marked loop back edges
- Proper handling of continue statements