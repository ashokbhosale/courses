File-Scoped Namespaces is a feature introduced in C# 10.0 and .NET 6.0 (which is part of .NET Core) that allows you to define namespaces directly within a file, without the need for enclosing `namespace` blocks. This feature aims to simplify namespace management and improve code readability by reducing boilerplate code.

Here's how you can use File-Scoped Namespaces in .NET Core C#:

1. **Defining File-Scoped Namespace**:

   To define a file-scoped namespace, you simply declare the namespace at the top of the file, without enclosing it within a `namespace` block. For example:

   ```csharp
   // File1.cs
   namespace MyNamespace;

   // Code within the file
   ```

   In this example, `MyNamespace` is a file-scoped namespace. All types defined within this file will belong to this namespace.

2. **Usage**:

   Once you've defined a file-scoped namespace in a file, all types declared within that file are implicitly part of that namespace. You don't need to specify the namespace explicitly for each type defined in the file.

   ```csharp
   // File1.cs
   namespace MyNamespace;

   class MyClass
   {
       // Class members
   }

   struct MyStruct
   {
       // Struct members
   }
   ```

   In this example, both `MyClass` and `MyStruct` are part of the `MyNamespace` namespace.

3. **Benefits**:

   - **Simplicity**: File-Scoped Namespaces simplify namespace management by eliminating the need for enclosing `namespace` blocks, reducing boilerplate code and improving code readability.
   
   - **Clarity**: By placing the namespace declaration at the top of the file, it's clear which namespace the types within the file belong to.

   - **Consistency**: File-Scoped Namespaces promote consistency by ensuring that each file explicitly declares its namespace, making it easier to understand the organization of types within a project.

   - **Reduced Scope**: File-Scoped Namespaces limit the scope of the namespace to the file in which it's declared, preventing accidental pollution of the global namespace.

4. **Compatibility**:

   File-Scoped Namespaces are fully compatible with existing C# code and namespaces. You can use them alongside traditional namespaces and `namespace` blocks within the same project.

File-Scoped Namespaces offer a simpler and more intuitive way to manage namespaces in C# code, making it easier to organize and understand the structure of your codebase. However, it's essential to use them judiciously and consider the implications on code organization and readability.