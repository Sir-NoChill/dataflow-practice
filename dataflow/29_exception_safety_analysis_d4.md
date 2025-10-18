# Problem 29: Exception Safety Dataflow Analysis (Difficulty: d4)

## Problem Statement

Analyze exception safety and resource cleanup in code with exceptions:

```
B1:  resource1 = acquire_resource()
     try_start
     goto B2

B2:  resource2 = acquire_resource()
     risky_operation()  // may throw
     goto B3

B3:  result = compute(resource1, resource2)
     release_resource(resource2)
     release_resource(resource1)
     try_end
     goto B6

B4:  // exception handler
     catch_start
     if resource2 != null:
         release_resource(resource2)
     if resource1 != null:
         release_resource(resource1)
     error_result = -1
     catch_end
     goto B6

B5:  // finally block (always executes)
     finally_start
     cleanup_globals()
     finally_end
     goto B6

B6:  return result
```

## Tasks

1. **Define exception safety analysis framework**:
   - How do you track resource acquisition and release?
   - How do exception edges affect resource lifetimes?
   - What constitutes a resource leak?

2. **Model exception control flow**:
   - How do try-catch-finally blocks affect the CFG?
   - Which program points are reachable via exception paths?

3. **Apply resource tracking analysis**:
   - Which resources are guaranteed to be released?
   - Where might resource leaks occur?
   - Are there any double-release errors?

4. **Exception safety verification**:
   - Is the code exception-safe (no resource leaks)?
   - What happens if an exception is thrown at different points?
   - Are there any missing cleanup paths?

5. **Optimization opportunities**: How can the analysis guide automatic resource management?

## Expected Output Format

- Exception-aware CFG
- Resource tracking analysis framework
- Analysis of resource lifetimes and cleanup
- Exception safety verification results
- Recommendations for improving exception safety