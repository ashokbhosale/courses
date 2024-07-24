Extension methods in C# .NET Core allow you to add new methods to existing types without modifying their source code. They provide a way to extend the functionality of classes, structs, interfaces, and other types without inheritance. Extension methods are defined as static methods within static classes and are typically used to add convenience methods or utility functions to existing types. Here's an overview of extension methods with examples in C# .NET Core:

1. **Syntax**:
   - Extension methods are static methods that are defined within a static class.
   - The first parameter of an extension method specifies the type that the method extends, preceded by the `this` keyword.
   - Extension methods must be in a non-nested, non-generic static class.

Example of defining an extension method:

```csharp
using System;

public static class StringExtensions
{
    public static bool IsNullOrEmpty(this string str)
    {
        return string.IsNullOrEmpty(str);
    }
}
```

2. **Usage**:
   - To use an extension method, simply import the namespace containing the extension method, and call it as if it were an instance method of the extended type.
   - The compiler automatically binds the call to the appropriate extension method based on the type of the first parameter.

Example of using an extension method:

```csharp
using System;

class Program
{
    static void Main()
    {
        string str = null;
        Console.WriteLine(str.IsNullOrEmpty()); // Output: True
    }
}
```

3. **Limitations**:
   - Extension methods cannot access private or protected members of the extended type.
   - They cannot be used to override existing methods or operators.
   - Extension methods are resolved statically at compile time, so they cannot be used to override virtual methods.

4. **Naming Convention**:
   - It's a common convention to name extension method classes with a name ending in "Extensions" and prefix extension methods with the extended type name.

Example of naming convention:

```csharp
public static class StringExtensions
{
    public static bool IsNullOrEmpty(this string str)
    {
        return string.IsNullOrEmpty(str);
    }
}
```

Extension methods are widely used in C# .NET Core for adding functionality to existing types, providing syntactic sugar, and improving code readability. They are commonly found in libraries, frameworks, and utility classes to enhance the capabilities of the .NET platform.