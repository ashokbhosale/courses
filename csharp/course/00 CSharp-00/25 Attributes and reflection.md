Attributes and reflection are powerful features in C# .NET Core that allow you to add metadata to types and members and inspect that metadata at runtime. Attributes provide a way to add declarative information to your code, and reflection enables you to dynamically inspect and manipulate types and members at runtime. Here's an overview of attributes and reflection with examples in .NET Core C#:

1. **Attributes**:
   - Attributes are declarative tags that you can apply to types, methods, properties, parameters, and other program elements.
   - They provide additional metadata about the code elements to which they are applied.
   - Attributes are defined using classes that derive from the `System.Attribute` base class.
   - You can create custom attributes by defining your own attribute classes.

Example of defining and using a custom attribute:

```csharp
using System;

[AttributeUsage(AttributeTargets.Method)]
public class MyCustomAttribute : Attribute
{
    public string Description { get; }

    public MyCustomAttribute(string description)
    {
        Description = description;
    }
}

class Program
{
    [MyCustom("This is a custom method attribute")]
    static void MyMethod()
    {
        Console.WriteLine("Executing MyMethod");
    }

    static void Main()
    {
        // Retrieving attributes using reflection
        var method = typeof(Program).GetMethod("MyMethod");
        var attribute = (MyCustomAttribute)Attribute.GetCustomAttribute(method, typeof(MyCustomAttribute));
        Console.WriteLine(attribute.Description);
    }
}
```

2. **Reflection**:
   - Reflection is the ability of a program to inspect its own structure and metadata at runtime.
   - It allows you to dynamically create instances of types, access and invoke methods, retrieve and set property values, and more.
   - Reflection is commonly used for tasks such as dependency injection, serialization, and dynamically loading assemblies.

Example of using reflection to inspect attributes:

```csharp
using System;
using System.Reflection;

class Program
{
    static void Main()
    {
        // Get the type of the Program class
        Type type = typeof(Program);

        // Iterate through methods and find those with MyCustomAttribute
        foreach (MethodInfo method in type.GetMethods())
        {
            if (method.IsDefined(typeof(MyCustomAttribute), inherit: true))
            {
                Console.WriteLine($"Method {method.Name} has MyCustomAttribute");
            }
        }
    }
}
```

In the above example, `typeof(Program)` retrieves the type metadata for the `Program` class, and `type.GetMethods()` retrieves an array of `MethodInfo` objects representing all methods of the class. We then iterate over these methods and check if each one has the `MyCustomAttribute` applied.

Attributes and reflection provide a powerful mechanism for adding metadata to your code and dynamically inspecting and manipulating it at runtime. They are commonly used in frameworks, libraries, and tools to enable various runtime behaviors and features.