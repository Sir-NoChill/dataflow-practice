# Problem 46: Complex Architectural Register Constraints

## Problem Statement
Handle register allocation with complex architectural constraints including instruction-specific register requirements.

## Three Address Code with Constraint Annotations
```
1:  dividend = 1000
2:  divisor = 7
3:  quotient, remainder = divide(dividend, divisor)  // x86: requires EAX/EDX
4:  shift_amount = 3
5:  shifted = arithmetic_shift(quotient, shift_amount)  // requires CL for shift amount
6:  multiplier = 100
7:  result = multiply_high(shifted, multiplier)     // x86: requires EAX/EDX
8:  string_src = "hello"
9:  string_dst = buffer
10: copy_result = string_copy(string_src, string_dst)  // x86: requires ESI/EDI
11: final = result + copy_result
12: return final
```

## Architectural Constraints
- Divide instruction: dividend in EAX, divisor anywhere, quotient in EAX, remainder in EDX
- Shift instruction: value anywhere, shift amount must be in CL register
- Multiply-high: operand in EAX, result high bits in EDX
- String operations: source in ESI, destination in EDI

## Task
1. Identify all instruction-specific register constraints
2. Model constraints in the interference graph construction
3. Handle precolored register requirements in allocation
4. Resolve conflicts between multiple constrained operations
5. Optimize allocation while satisfying all architectural constraints

## Expected Output Format
- Complete constraint analysis for each operation
- Modified interference graph incorporating constraints
- Constraint resolution strategy
- Final register allocation satisfying all requirements
- Analysis of constraint impact on allocation quality