# Problem 45: Hot/Cold Code-Aware Register Allocation

## Problem Statement
Apply register allocation strategies that differentiate between hot (frequently executed) and cold (rarely executed) code regions.

## Three Address Code with Execution Frequency Annotations
```
1:  x = input              // HOT: executed 1M times
2:  if x > 0 goto 5        // HOT: branch taken 90% of time
3:  error_code = -1        // COLD: executed 100K times
4:  goto error_handler     // COLD: executed 100K times
5:  y = x * 2              // HOT: executed 900K times
6:  z = fast_path(y)       // HOT: function call, executed 900K times
7:  if z > 100 goto 10     // HOT: branch taken 10% of time
8:  result = z + 1         // HOT: executed 810K times
9:  goto 12                // HOT: executed 810K times
10: result = expensive_computation(z)  // WARM: executed 90K times
11: goto 12                // WARM: executed 90K times
12: return result          // HOT: executed 900K times

error_handler:             // COLD: entire block executed 100K times
13: log_error(error_code)
14: cleanup_resources()
15: return -1
```

## Task
1. Classify code regions by execution frequency (hot/warm/cold)
2. Apply different register allocation strategies per region:
   - Hot code: minimize spills, optimize for speed
   - Cold code: minimize register usage, allow more spills
   - Transition regions: balance between strategies
3. Handle register allocation across hot/cold boundaries
4. Optimize global allocation considering frequency weights
5. Estimate performance improvement from frequency-aware allocation

## Expected Output Format
- Code region classification by execution frequency
- Different allocation strategies per frequency class
- Boundary handling between hot/cold regions
- Global allocation optimization with frequency weighting
- Performance estimation and improvement analysis