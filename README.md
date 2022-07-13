# SAFE_CALL

This simple library allows you to protect yourself against reverse engineers.

Usage:
``` cs
_.SAFE_CALL(typeof(Console), "WriteLine", "Hello World!");
```


Internals of what the library does:
1. Check if the function you are trying to call is hooked
2. Check if IsDebuggerPresent is hooked and also check what it returns.
3. Create a DynamicMethod and copy over the il code generated by the disassembler (essentially making a shadow-copy).
4. Invoke the new shadow-copy and return its output.
