Extension methods in .NET Core C# provide a way to add new methods to existing types without modifying the original type's source code. They are static methods that are called as if they were instance methods of the extended type. Here's how you can use extension methods in .NET Core:

### 1. Syntax:

An extension method is defined as a static method within a static class. The first parameter of the method specifies the type being extended, preceded by the `this` keyword.

```csharp
public static class MyExtensions
{
    public static ReturnType MyExtensionMethod(this ExtendedType extendedParameter, other parameters...)
    {
        // Method implementation
    }
}
```

### 2. Usage:

Once defined, extension methods can be used as if they were instance methods of the extended type. You don't need to create an instance of the static class; instead, you just call the method directly on an instance of the extended type.

```csharp
using MyExtensionsNamespace;

// Usage of extension method
ExtendedType instance = new ExtendedType();
instance.MyExtensionMethod(parameters);
```

### 3. Example:

```csharp
namespace MyExtensionsNamespace
{
    public static class StringExtensions
    {
        public static string CustomToUpper(this string input)
        {
            return input.ToUpper() + " (customized)";
        }
    }
}
```

### 4. Limitations:

- Extension methods cannot access private members of the extended type.
- They cannot override existing methods.
- They must be defined in a static class.
- They cannot be used to add instance fields or properties to the extended type.

### 5. Using Extension Methods from Other Assemblies:

To use extension methods defined in another assembly, you need to import the namespace where the extension method is defined.

### Summary:

Extension methods in .NET Core C# provide a convenient way to extend the functionality of existing types without modifying their source code. By understanding their syntax and usage, you can enhance code reusability and readability in your .NET Core projects. Let me know if you need further assistance or examples!