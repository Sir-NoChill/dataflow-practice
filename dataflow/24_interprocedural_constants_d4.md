# Problem 24: Interprocedural Constant Propagation (Difficulty: d4)

## Problem Statement

Analyze constant propagation across function boundaries with different calling contexts:

```
function main():
B1:  x = 5
     y = compute(x, 10)
     z = compute(x, 20)  // same function, different args
     result = y + z
     return result

function compute(a, b):
B2:  if a > 0:
         c = a + b
         d = helper(c)
     else:
         c = a - b
         d = helper(c)
     return d

function helper(param):
B3:  if param > 15:
         return param * 2
     else:
         return param + 1
```

## Tasks

1. **Model calling contexts**:
   - How do you handle the same function called with different argument values?
   - Should `compute(5, 10)` and `compute(5, 20)` be analyzed separately?

2. **Define interprocedural constant propagation framework**:
   - How do you propagate constants through parameter passing?
   - How do you handle return values with different constant states?

3. **Apply context-sensitive analysis**:
   - Trace the constant values through both calls to `compute`
   - Show how different calling contexts lead to different constant information

4. **Optimization opportunities**:
   - Which function calls can be specialized based on constant arguments?
   - Which conditional branches can be eliminated in called functions?
   - Can any function calls be inlined and then optimized?

5. **Scalability considerations**: How does context sensitivity affect analysis complexity?

## Expected Output Format

- Context-sensitive analysis framework
- Separate analysis for each calling context
- Constant propagation results for each function call
- List of optimization opportunities enabled by interprocedural analysis
- Discussion of scalability trade-offs