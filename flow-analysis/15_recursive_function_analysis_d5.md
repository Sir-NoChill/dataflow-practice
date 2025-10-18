# Recursive Function Analysis

## Problem Statement
Analyze the following mutually recursive functions for dataflow properties and optimization opportunities.

## Three-Address Code
```
// Function factorial(n)
factorial:
    if n <= 1 goto L1
    temp1 = n - 1
    temp2 = call factorial(temp1)
    result = n * temp2
    return result
L1: return 1

// Function fibonacci(n)
fibonacci:
    if n <= 1 goto L2
    temp1 = n - 1
    temp2 = n - 2
    val1 = call fibonacci(temp1)
    val2 = call fibonacci(temp2)
    result = val1 + val2
    return result
L2: return n

// Function isEven(x)
isEven:
    if x == 0 goto L3
    temp = x - 1
    result = call isOdd(temp)
    return result
L3: return 1

// Function isOdd(x)
isOdd:
    if x == 0 goto L4
    temp = x - 1
    result = call isEven(temp)
    return result
L4: return 0

// Function process(data, count)
process:
    if count <= 0 goto L5
    newData = transform(data)
    newCount = count - 1
    if shouldRecurse(newData) goto L6
    return newData
L6: result = call process(newData, newCount)
    return result
L5: return data
```

## Tasks
1. Identify all recursive calling patterns (direct, indirect, mutual)
2. Analyze termination conditions and base cases
3. Determine tail recursion optimization opportunities
4. Model the effect of recursion on dataflow analysis precision
5. Propose memoization or iterative transformation strategies

## Expected Output Format
- Classification of recursion types for each function
- Termination analysis and base case identification
- Tail recursion optimization candidates
- Impact assessment on dataflow analysis convergence
- Transformation strategies for optimization