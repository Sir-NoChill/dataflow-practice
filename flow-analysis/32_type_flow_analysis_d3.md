# Type Flow Analysis

## Problem Statement
Perform type flow analysis on dynamically typed code to enable type-based optimizations.

## Three-Address Code
```
B1: obj = input_dynamic()
    if typeof(obj) == "int" goto B2
    if typeof(obj) == "float" goto B3
    goto B4
B2: int_result = obj + 42      // obj is definitely int
    obj = int_result           // obj becomes int
    goto B5
B3: float_result = obj * 3.14  // obj is definitely float
    obj = float_result         // obj becomes float
    goto B5
B4: str_result = obj + "text"  // obj is string or other
    obj = str_result           // obj becomes string
    goto B5
B5: if loop_condition goto B6
    goto B7
B6: temp = transform(obj)      // obj type is unknown here
    obj = temp                 // type depends on transform
    goto B1
B7: return obj
```

## Tasks
1. Track type information flow through variable assignments
2. Handle type narrowing through conditional branches
3. Analyze type widening at merge points
4. Identify opportunities for type-specialized code generation
5. Model the effect of polymorphic operations on type precision

## Expected Output Format
- Type lattice definition for the analysis
- Type sets at each program point
- Type narrowing and widening analysis
- Specialization opportunities identification
- Precision loss analysis at merge points