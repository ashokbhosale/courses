**Understanding .NET Core:**

.NET Core is a cross-platform, open-source framework for building modern, scalable, and high-performance applications. It is a successor to the .NET Framework and is designed to be modular, lightweight, and optimized for cloud-native development. .NET Core allows developers to build applications that can run on Windows, macOS, and Linux, making it ideal for building cross-platform solutions.

**Installing and Setting up the .NET Core SDK:**

To install the .NET Core SDK, follow these steps:

1. Visit the official .NET Core website: [dotnet.microsoft.com/download](https://dotnet.microsoft.com/download)
2. Download the appropriate installer for your operating system (Windows, macOS, or Linux).
3. Follow the installation instructions provided by the installer.
4. Once installed, open a command prompt or terminal and run the following command to verify the installation:

```
dotnet --version
```

This command should display the installed version of the .NET Core SDK.

**Creating Your First .NET Core Project using CLI:**

To create your first .NET Core project using the command-line interface (CLI), follow these steps:

1. Open a command prompt or terminal.
2. Navigate to the directory where you want to create your project.
3. Run the following command to create a new console application:

```
dotnet new console -n MyFirstApp
```

This command creates a new directory named "MyFirstApp" containing the files for a simple console application.

4. Navigate into the newly created directory:

```
cd MyFirstApp
```

5. Run the following command to build and run the application:

```
dotnet run
```

This command will compile the application and execute the default entry point (usually the `Main` method) of the application.

**Example:**

Here's an example of a simple "Hello, World!" application in C# using .NET Core:

```csharp
using System;

class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine("Hello, World!");
    }
}
```

After creating the project and running the `dotnet run` command, you should see the output "Hello, World!" printed in the console.

With these steps, you've created your first .NET Core project using the command-line interface, demonstrating the ease of setup and development with .NET Core.