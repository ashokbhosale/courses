Global Usings is a feature introduced in C# 10.0 and .NET 6.0 (which is part of .NET Core) that allows you to import namespaces globally for all files within a project or a directory. This feature simplifies the process of importing commonly used namespaces, reducing boilerplate code and improving readability.

Here's how you can use Global Usings in .NET Core C#:

1. **Enabling Global Usings**:

   You can enable Global Usings in your project by adding the `globalUsings` element to your project file (`.csproj`) and specifying the namespaces you want to import globally. For example:

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

       <PropertyGroup>
           <OutputType>Exe</OutputType>
           <TargetFramework>net6.0</TargetFramework>
       </PropertyGroup>

       <ItemGroup>
           <GlobalUsings>
               <Using>System</Using>
               <Using>System.Collections.Generic</Using>
               <Using>System.Linq</Using>
               <!-- Add more namespaces as needed -->
           </GlobalUsings>
       </ItemGroup>

   </Project>
   ```

2. **Using Global Usings in Code**:

   Once you've specified global usings in your project file, you can directly use types from the specified namespaces in your code without explicitly importing them using `using` directives. For example:

   ```csharp
   using System;

   class Program
   {
       static void Main()
       {
           // You can directly use types from System namespace without importing it
           Console.WriteLine("Hello, World!");
       }
   }
   ```

   With global usings enabled, you don't need to explicitly import `System` namespace using a `using` directive in every file where you use types from that namespace.

3. **Directory-based Global Usings**:

   In addition to project-level global usings, you can also specify global usings at the directory level by creating a `GlobalUsings.cs` file in the directory and adding the desired `using` directives. All C# files within that directory (and its subdirectories) will automatically inherit these global usings.

   ```csharp
   // GlobalUsings.cs
   global using System;
   global using System.Collections.Generic;
   ```

   This approach is useful when you want to apply different sets of global usings to different parts of your project.

Global Usings help streamline the codebase by reducing the clutter of repetitive `using` directives, especially for commonly used namespaces. However, it's essential to use them judiciously and avoid cluttering the global namespace with unnecessary imports.