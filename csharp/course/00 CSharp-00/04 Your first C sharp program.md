Sure! Here's a simple "Hello, World!" program written in C# using .NET Core:

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

Let's break down the different parts of this program:

- `using System;`: This line tells the compiler to include the `System` namespace, which contains fundamental types and classes provided by the .NET Core framework.

- `class Program`: This defines a class named `Program`. In C#, the entry point of a program is typically the `Main` method within a class named `Program`.

- `static void Main(string[] args)`: This is the entry point of the program. It is a static method named `Main`, which accepts an array of strings (`args`) as parameters. The `Main` method is where the program starts executing.

- `Console.WriteLine("Hello, World!");`: This line writes the string "Hello, World!" to the console output. The `Console.WriteLine` method is used to print text to the console.

To run this program:

1. Make sure you have the .NET Core SDK installed on your system. You can download it from the official .NET website: https://dotnet.microsoft.com/download

2. Create a new directory for your project and navigate into it using the command line.

3. Create a new C# file (e.g., `Program.cs`) and paste the code snippet above into the file.

4. Open a terminal or command prompt in the directory containing your C# file.

5. Run the following command to compile and execute the program:

   ```
	 dotnet run
   ```

You should see the output "Hello, World!" printed to the console.

Congratulations! You've just created and run your first C# program using .NET Core.