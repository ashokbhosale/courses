Encapsulation and access modifiers are key concepts in C# .NET Core that help organize and protect your code by controlling access to members of classes and struct. Here's an overview of encapsulation and access modifiers:

1. **Encapsulation**:
   - Encapsulation is the bundling of data (attributes or fields) and methods (functions or procedures) that operate on the data into a single unit called a class.
   - It allows for the hiding of internal state and requiring all interactions to occur through well-defined interfaces (public methods), promoting modularity and ease of maintenance.
   - Encapsulation prevents the direct access to internal data of a class by external code, enforcing access through defined methods, which may include validation and other logic.
   - It helps in achieving data abstraction, data hiding, and information hiding, which are essential principles in object-oriented programming.

2. **Access Modifiers**:
   - Access modifiers control the accessibility of classes, members (fields, properties, methods, and events), and types (classes, structs, interfaces, and enums) in C#.
   - There are five access modifiers in C#:
     - **public**: The member is accessible from any other code in the same assembly or another assembly that references it.
     - **private**: The member is accessible only within the body of the class or struct in which it is declared.
     - **protected**: The member is accessible only within its class or by derived classes.
     - **internal**: The member is accessible only within the same assembly.
     - **protected internal**: The member is accessible within its assembly and by derived classes, whether they are in the same assembly or a different assembly.
   - You can apply access modifiers to classes, class members, and nested types to control their visibility and accessibility from other parts of the program.

Example:

```csharp
public class MyClass
{
    private int myPrivateField;
    public int MyPublicField;

    private void MyPrivateMethod()
    {
        // Code here
    }

    public void MyPublicMethod()
    {
        // Code here
    }
}
```

In this example, `myPrivateField` and `MyPrivateMethod()` are private and can only be accessed within the `MyClass`. `MyPublicField` and `MyPublicMethod()` are public and can be accessed from any code that has access to an instance of `MyClass`.

Encapsulation and access modifiers help in creating maintainable, secure, and well-structured code in C# .NET Core applications. They promote code reusability, flexibility, and security by controlling access to class members.