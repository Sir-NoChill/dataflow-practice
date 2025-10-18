# Problem 23: Interprocedural Reaching Definitions (Difficulty: d4)

## Problem Statement

Perform reaching definitions analysis across function boundaries:

```
function main():
B1:  x = 10
     y = 20
     call foo(x, y)  // modifies global g
     z = g + x       // g modified by foo
     return z

function foo(a, b):
B2:  global g
     g = a + b
     temp = g * 2
     call bar(temp)  // may modify g again
     g = g + 1
     return

function bar(param):
B3:  global g
     if param > 50:
         g = param
     else:
         g = 0
     local_var = g + 10  // dead variable
     return
```

## Tasks

1. **Model the interprocedural CFG**:
   - How do you represent function calls and returns?
   - How do parameter passing and global variables affect the analysis?

2. **Define interprocedural reaching definitions framework**:
   - How do you handle function call sites?
   - How do you model parameter binding?
   - How do you handle global variable modifications?

3. **Apply the analysis**:
   - Which definitions of `g` reach the use `z = g + x` in main?
   - How do you handle the uncertainty in `bar` about which path modifies `g`?

4. **Compare approaches**:
   - Context-sensitive vs. context-insensitive analysis
   - How would function summaries improve precision?

5. **Optimization implications**: What optimizations are enabled or hindered by interprocedural analysis?

## Expected Output Format

- Interprocedural CFG description
- Framework definition with call/return handling
- Analysis results showing cross-function definition flows
- Comparison of different interprocedural approaches
- Discussion of optimization opportunities and challenges