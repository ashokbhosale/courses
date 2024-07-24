String interpolation in .NET Core C# provides a more readable and concise syntax for formatting strings compared to traditional string concatenation or composite formatting. It allows you to embed expressions directly within a string literal, making the code easier to understand and maintain. Here's how you can use string interpolation in .NET Core C#:

### Syntax:

String interpolation is achieved by prefixing a string literal with the `$` symbol, followed by curly braces `{}` containing the expressions you want to interpolate.

```csharp
string name = "John";
int age = 30;

// String interpolation
string message = $"My name is {name} and I am {age} years old.";
```

### Example:

```csharp
string name = "Alice";
int score = 85;

// String interpolation with expressions
string result = $"{name} scored {score}% in the exam.";

// Output: "Alice scored 85% in the exam."
```

### Format Specifiers:

You can also apply format specifiers within the curly braces to format the interpolated expressions.

```csharp
decimal price = 99.99m;

// Currency formatting
string formattedPrice = $"Price: {price:C}";

// Output: "Price: $99.99"
```

### Escaping Characters:

You can escape characters within the interpolated string using the backslash `\` character.

```csharp
string filePath = @"C:\Documents";

// Escaping characters
string message = $"The file is located at: {filePath}";
```

### Benefits:

- Improved readability: String interpolation makes the code easier to understand by embedding expressions directly within the string.
- Reduced boilerplate code: String interpolation eliminates the need for explicit concatenation or formatting operations, resulting in cleaner code.

### Summary:

String interpolation in .NET Core C# provides a more readable and concise syntax for formatting strings compared to traditional string concatenation or composite formatting. By using string interpolation, you can make your code more expressive and maintainable in your .NET Core projects. Let me know if you need further assistance or examples!