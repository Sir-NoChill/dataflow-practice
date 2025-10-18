# Problem 32: Register Allocation with Memory Operand Flexibility

## Problem Statement
Optimize register allocation when the target architecture supports memory operands in arithmetic operations.

## Three Address Code
```
1:  a = load mem1
2:  b = load mem2
3:  c = a + b
4:  d = c * 2
5:  e = d + a
6:  f = e + b
7:  store f, mem3
8:  return
```

## Architecture Capabilities
- Arithmetic operations can use memory operands: `add reg, mem` or `add mem, reg`
- Memory operands reduce register pressure but have higher latency
- Each instruction can have at most one memory operand

## Task
1. Identify opportunities to use memory operands instead of registers
2. Modify the interference graph to account for memory operand options
3. Apply register allocation with memory operand considerations
4. Balance register pressure vs memory access latency
5. Show the final code with optimal register/memory operand mix

## Expected Output Format
- Analysis of memory operand opportunities
- Modified register allocation considering memory options
- Trade-off analysis: register pressure vs memory latency
- Final code generation with memory operands
- Performance estimation for the allocation strategy