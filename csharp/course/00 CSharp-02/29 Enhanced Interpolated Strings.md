Enhanced Interpolated Strings were introduced in C# 10.0, which is part of .NET 6.0 (including .NET Core). This feature enhances the capabilities of interpolated strings by providing additional formatting options and expressions directly within the interpolated string syntax. Here are the key enhancements:

1. **Alignment and Format Strings**:
   
   Enhanced interpolated strings allow specifying alignment and format strings directly within the interpolation expression. This provides more control over how the interpolated value is formatted within the string.

   ```csharp
   int number = 42;
   string formattedString = $"{number,5}"; // Right-aligned, padded to 5 characters
   ```

2. **Conditional Expressions**:

   You can now use conditional expressions (`? :`) directly within the interpolation expression to conditionally include values in the string.

   ```csharp
   bool condition = true;
   string result = $"{condition ? "Yes" : "No"}";
   ```

3. **String Interpolation Inside Expressions**:

   Enhanced interpolated strings allow using interpolated strings within other expressions, providing more flexibility in composing complex string values.

   ```csharp
   string name = "John";
   string message = $"Hello, {name.ToUpper()}!";
   ```

4. **Format String Alignment**:

   You can specify alignment and format strings directly within the interpolation expression using colon `:` syntax.

   ```csharp
   double price = 123.456;
   string formattedPrice = $"{price:C2}"; // Currency format with 2 decimal places
   ```

5. **Digit Separator in Numeric Interpolations**:

   Numeric interpolations within enhanced interpolated strings can now include digit separators (underscore `_`) for better readability.

   ```csharp
   int largeNumber = 1_000_000;
   string formattedNumber = $"{largeNumber:N0}"; // Number format with thousands separator
   ```

These enhancements make interpolated strings more powerful and expressive, allowing for more flexible string formatting and composition directly within the string interpolation syntax. They improve readability and maintainability of code that involves string formatting and concatenation.