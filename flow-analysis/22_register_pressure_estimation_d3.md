# Register Pressure Estimation

## Problem Statement
Estimate register pressure and identify spill candidates for the following code with limited register resources.

## Three-Address Code
```
B1: a = input1
    b = input2
    c = input3
    d = a + b
    e = c * 2
    goto B2
B2: if d > e goto B3
    goto B4
B3: f = a * c
    g = b + e
    h = f - g
    i = h / 2
    goto B5
B4: f = a - b
    g = c + d
    h = e * f
    i = g + h
    goto B5
B5: j = i + a
    k = j - b
    l = k + c
    m = l * d
    n = m + e
    if n > 100 goto B6
    goto B2
B6: result = n + f + g
    return result
```

## Given Constraints
- Target architecture has 8 general-purpose registers
- Variables a, b, c must remain in registers (frequently accessed)
- Register allocation should minimize spill code

## Tasks
1. Perform live variable analysis to determine live ranges
2. Calculate register pressure at each program point
3. Identify points where register pressure exceeds available registers
4. Select spill candidates based on live range characteristics
5. Estimate the cost of different spilling strategies

## Expected Output Format
- Live variable analysis results
- Register pressure graph through the program
- Spill pressure points identification
- Spill candidate ranking with cost analysis
- Optimal spilling strategy with estimated performance impact