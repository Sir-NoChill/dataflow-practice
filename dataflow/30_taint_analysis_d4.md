# Problem 30: Taint Analysis for Security (Difficulty: d4)

## Problem Statement

Perform taint analysis to track potentially unsafe data flows:

```
B1:  user_input = get_user_input()    // TAINTED SOURCE
     safe_constant = 42
     goto B2

B2:  if user_input > 0 goto B3 else goto B4

B3:  sanitized = sanitize(user_input)  // SANITIZATION FUNCTION
     processed = sanitized + safe_constant
     goto B5

B4:  processed = user_input * 2        // STILL TAINTED
     goto B5

B5:  if processed > 100 goto B6 else goto B7

B6:  database_query(processed)         // SENSITIVE SINK - SQL injection risk?
     goto B8

B7:  log_message(processed)            // SENSITIVE SINK - log injection risk?
     goto B8

B8:  return processed
```

## Tasks

1. **Define taint analysis framework** by specifying:
   - The domain (tainted/untainted/sanitized states)
   - How taint propagates through operations
   - Sources of taint (user input, network data, etc.)
   - Sinks where tainted data is dangerous
   - Sanitization functions that remove taint

2. **Apply taint analysis** to track data flow:
   - Which variables become tainted?
   - How does taint propagate through arithmetic operations?
   - Where does sanitization occur?

3. **Identify security vulnerabilities**:
   - Which sinks receive tainted data?
   - Are there any unsanitized paths from sources to sinks?
   - Which branches are safe vs. unsafe?

4. **Propose security fixes**:
   - Where should additional sanitization be added?
   - Which operations need input validation?
   - How can the code be restructured for better security?

## Expected Output Format

- Taint analysis framework with propagation rules
- Complete taint tracking through all program paths
- Identification of security vulnerabilities
- Recommended security improvements