Auto-property initializers in .NET Core C# allow you to specify default values for auto-implemented properties directly within their declaration. This simplifies the initialization of properties and reduces boilerplate code. Here's how you can use auto-property initializers in .NET Core C#:

### Syntax:

Auto-property initializers are specified directly after the property declaration and are assigned using the `=` operator.

```csharp
public class MyClass
{
    public int MyProperty { get; set; } = defaultValue;
}
```

### Example:

```csharp
public class Person
{
    public string Name { get; set; } = "John Doe";
    public int Age { get; set; } = 30;
}
```

### Benefits:

1. **Simplified Initialization**: Auto-property initializers allow you to provide default values for properties without the need for a constructor or explicit assignment.

2. **Reduced Boilerplate Code**: By specifying default values directly within the property declaration, you reduce the amount of boilerplate code required in your class.

### Usage Considerations:

- Auto-property initializers are only available for auto-implemented properties, not for properties with custom getters and setters.

- The order of initialization is important. If there are dependencies between properties, ensure that they are initialized in the correct order.

### Summary:

Auto-property initializers in .NET Core C# provide a convenient way to specify default values for auto-implemented properties directly within their declaration. By using auto-property initializers, you can simplify property initialization and reduce boilerplate code in your .NET Core projects. Let me know if you need further assistance or examples!