# Taint Analysis for Security

## Problem Statement
Implement taint analysis to track potentially unsafe data flow from untrusted sources.

## Three-Address Code
```
B1: user_input = read_untrusted()    // taint source
    safe_data = constant_value
    goto B2
B2: if validate(user_input) goto B3
    goto B7
B3: sanitized = sanitize(user_input) // taint sink/sanitization
    processed = transform(sanitized)
    goto B4
B4: if condition goto B5
    goto B6
B5: mixed = safe_data + processed    // safe + sanitized
    query = build_sql(mixed)         // potential taint sink
    result = execute_query(query)
    goto B8
B6: direct_query = build_sql(user_input) // UNSAFE: direct taint flow
    result = execute_query(direct_query)  // taint sink
    goto B8
B7: error_log(user_input)            // logging untrusted data
    result = default_result
    goto B8
B8: return result
```

## Tasks
1. Identify taint sources, sinks, and sanitization points
2. Track taint propagation through data flow
3. Detect potential security vulnerabilities
4. Analyze the effect of sanitization on taint removal
5. Identify safe vs unsafe execution paths

## Expected Output Format
- Taint source and sink identification
- Taint propagation analysis through the program
- Security vulnerability detection (SQL injection, XSS, etc.)
- Sanitization effectiveness analysis
- Safe execution path verification