C# has continuously evolved its pattern matching capabilities with each new version, including enhancements introduced in .NET Core. Some of the enhancements include new patterns, refinements in syntax, and improvements in usability. Here are some of the pattern matching enhancements in .NET Core C#:

1. **Relational Patterns**:
   
   Introduced in C# 8.0, relational patterns allow you to match values against relational operators (<, <=, >, >=, ==, !=). For example:

   ```csharp
   if (number is >= 0 and <= 100)
   {
       // Do something
   }
   ```

2. **Logical Patterns**:
   
   C# 9.0 introduced logical patterns, which enable combining multiple patterns using logical operators (&&, ||, !). For example:

   ```csharp
   if (obj is not null and string s)
   {
       // obj is not null and is a string
   }
   ```

3. **Parenthesized Patterns**:

   Parenthesized patterns allow grouping patterns to clarify precedence. This is particularly useful when combining multiple patterns with logical operators. For example:

   ```csharp
   if ((obj is string s || obj is int) && s.Length > 5)
   {
       // Do something
   }
   ```

4. **Property Patterns Enhancements**:

   Property patterns, introduced in C# 8.0, allow matching against properties of objects. In .NET Core C#, property patterns were enhanced to support recursive patterns, allowing for more expressive matching. For example:

   ```csharp
   if (point is { X: var x, Y: var y } && x > 0 && y > 0)
   {
       // point is in the first quadrant
   }
   ```

5. **Wildcard Patterns**:

   C# 9.0 introduced the wildcard pattern (`_`), which matches any value but doesn't bind it to a variable. It's particularly useful when you want to ignore certain values. For example:

   ```csharp
   if (obj is not null and _)
   {
       // Do something
   }
   ```

These enhancements make pattern matching in C# more powerful, expressive, and easier to use. They allow developers to write more concise and readable code when dealing with complex conditional logic and data structures.