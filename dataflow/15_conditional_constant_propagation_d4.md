# Problem 15: Advanced Conditional Constant Propagation with Function Calls (Difficulty: d4)

## Problem Statement

Analyze conditional constant propagation in the presence of function calls and global variables:

```
// Global variables
global_var = 100

B1:  x = 5
     y = global_var
     call init_globals()  // may modify global_var
     z = global_var
     goto B2

B2:  if x == 5 goto B3 else goto B4

B3:  a = pure_function(x)  // pure function, no side effects
     b = y + a
     call modify_global(10)  // modifies global_var to parameter value
     goto B5

B4:  a = 20
     b = z + a
     goto B5

B5:  c = global_var
     d = a + b + c
     if d > 50 goto B6 else goto B7

B6:  result = pure_function(a) + c
     goto B8

B7:  result = b + c
     goto B8

B8:  return result
```

## Tasks

1. **Define the framework** accounting for:
   - Function calls with side effects
   - Pure functions vs. impure functions
   - Global variable modifications

2. **Model function effects**:
   - How do you handle `init_globals()` which may modify globals?
   - How can `pure_function()` be optimized?
   - What can be inferred about `modify_global(10)`?

3. **Apply the analysis** with careful tracking of:
   - When global variables become non-constant
   - How function calls affect the lattice values
   - Which paths through the program maintain constant information

4. **Interprocedural considerations**:
   - What assumptions must be made about called functions?
   - How would having function summaries improve the analysis?

5. **Advanced optimizations**: What optimizations are possible given different assumptions about function behavior?

## Expected Output Format

- Framework definition with function call handling
- Analysis results with discussion of assumptions
- Comparison of optimization potential under different function behavior assumptions
- Discussion of interprocedural analysis benefits