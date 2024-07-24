Pattern Matching in C# has seen continuous enhancements with each new version, including improvements in .NET Core. Here are some of the notable enhancements and features introduced in recent versions of C# and .NET Core:

1. **Relational Patterns (C# 8.0)**:
   - Allows matching values against relational operators (`<`, `<=`, `>`, `>=`, `==`, `!=`).
   - Example: `if (number is >= 0 and <= 100) { /* Do something */ }`.

2. **Logical Patterns (C# 9.0)**:
   - Enables combining multiple patterns using logical operators (`&&`, `||`, `!`).
   - Example: `if (obj is not null and string s) { /* Do something */ }`.

3. **Parenthesized Patterns (C# 9.0)**:
   - Allows grouping patterns using parentheses to clarify precedence.
   - Example: `if ((obj is string s || obj is int) && s.Length > 5) { /* Do something */ }`.

4. **Wildcard Patterns (C# 9.0)**:
   - Introduces the wildcard pattern (`_`) to match any value without binding it to a variable.
   - Example: `if (obj is not null and _) { /* Do something */ }`.

5. **Property Patterns Enhancements (C# 8.0 and C# 9.0)**:
   - Supports recursive patterns, allowing more expressive matching.
   - Example: `if (point is { X: var x, Y: var y } && x > 0 && y > 0) { /* Do something */ }`.

6. **Type Patterns Enhancements (C# 9.0)**:
   - Improvements in the syntax for type patterns.
   - Example: `if (obj is string s) { /* Do something */ }`.

7. **Switch Expressions Enhancements (C# 8.0 and C# 9.0)**:
   - Allows using patterns in switch expressions for concise and expressive code.
   - Example: `string result = obj switch { string s => s.ToUpper(), int i => i.ToString(), _ => "Unknown" };`.

8. **Extending Pattern Matching to Interfaces and Abstract Classes (C# 9.0)**:
   - Enables matching against members of interfaces and abstract classes.
   - Example: `if (shape is ICircle { Radius: > 0 }) { /* Do something */ }`.

These enhancements make pattern matching in C# more powerful, expressive, and easier to use, allowing developers to write concise and readable code for complex conditional logic and data structures. They significantly improve the language's capabilities in handling diverse scenarios effectively.