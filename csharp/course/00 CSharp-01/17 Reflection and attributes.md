Reflection and attributes are powerful features in .NET Core C# that allow you to inspect and manipulate code at runtime, as well as attach metadata to types and members. Here's an overview of how you can use reflection and attributes in .NET Core C#:

### Reflection

Reflection allows you to inspect and manipulate types, methods, properties, fields, and other members of assemblies at runtime.

#### Inspecting Types

```csharp
using System;
using System.Reflection;

class Program
{
    static void Main()
    {
        Type type = typeof(string);
        Console.WriteLine($"Type Name: {type.Name}");
        Console.WriteLine($"Full Name: {type.FullName}");

        MethodInfo[] methods = type.GetMethods();
        foreach (MethodInfo method in methods)
        {
            Console.WriteLine($"Method: {method.Name}");
        }
    }
}
```

#### Invoking Methods Dynamically

```csharp
using System;
using System.Reflection;

class Program
{
    static void Main()
    {
        Type type = typeof(Console);
        MethodInfo method = type.GetMethod("WriteLine", new[] { typeof(string) });
        method.Invoke(null, new object[] { "Hello, World!" });
    }
}
```

### Attributes

Attributes allow you to attach metadata to types and members to provide additional information to the compiler or runtime.

#### Defining Custom Attributes

```csharp
using System;

[AttributeUsage(AttributeTargets.Class | AttributeTargets.Method)]
public class MyAttribute : Attribute
{
    public string Description { get; }

    public MyAttribute(string description)
    {
        Description = description;
    }
}
```

#### Using Custom Attributes

```csharp
[My("This is a class attribute.")]
class MyClass
{
    [My("This is a method attribute.")]
    public void MyMethod()
    {
        // Method implementation
    }
}
```

#### Retrieving Attribute Information

```csharp
class Program
{
    static void Main()
    {
        Type type = typeof(MyClass);
        MyAttribute classAttribute = (MyAttribute)Attribute.GetCustomAttribute(type, typeof(MyAttribute));
        Console.WriteLine($"Class Attribute: {classAttribute.Description}");

        MethodInfo method = type.GetMethod("MyMethod");
        MyAttribute methodAttribute = (MyAttribute)Attribute.GetCustomAttribute(method, typeof(MyAttribute));
        Console.WriteLine($"Method Attribute: {methodAttribute.Description}");
    }
}
```

Reflection and attributes are commonly used in frameworks and libraries to implement features like dependency injection, serialization, and metadata-driven behaviors. However, they should be used judiciously due to their runtime overhead and potential complexity. Let me know if you need further clarification or more examples!