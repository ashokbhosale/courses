**.NET Core Fundamentals:**

.NET Core is a cross-platform, open-source framework for building modern, high-performance applications. Understanding its core components is essential for working effectively with .NET Core.

**1. Common Language Runtime (CLR):**

The Common Language Runtime (CLR) is the execution engine responsible for running .NET Core applications. It provides various services, including memory management, garbage collection, exception handling, and security. The CLR also ensures that .NET Core applications can run on different operating systems by providing a common runtime environment.

**2. Class Libraries:**

Class libraries are collections of reusable code components that provide common functionality to .NET Core applications. These libraries contain classes, interfaces, and other types that developers can use to build their applications more efficiently. Examples of class libraries in .NET Core include the Base Class Library (BCL) and various third-party libraries available through NuGet.

**3. Global Assembly Cache (GAC):**

The Global Assembly Cache (GAC) is a shared location on the system where .NET Core assemblies (DLL files) are stored for use by multiple applications. However, in .NET Core, the GAC is not used as extensively as in the traditional .NET Framework. Instead, dependencies are typically managed using project-specific dependencies and package managers like NuGet.

**Example:**

In a .NET Core application, you typically interact with these components indirectly through your code. For example, consider the following C# code snippet:

```csharp
using System;

class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine("Hello, .NET Core!");
    }
}
```

In this example:
- `System` is a namespace that contains fundamental types and base types that define commonly used value and reference data types, events, and interfaces.
- `Console` is a class in the `System` namespace that provides methods for reading from and writing to the console.
- `WriteLine` is a method of the `Console` class used to display a line of text on the console.

When you run this .NET Core application, the CLR executes the code, and the necessary class libraries are automatically loaded to provide the required functionality. You don't need to directly interact with the CLR or manage assemblies in the GAC in most cases, as these tasks are handled by the .NET Core runtime environment.