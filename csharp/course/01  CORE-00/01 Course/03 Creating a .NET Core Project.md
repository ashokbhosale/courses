To create a basic .NET Core application, you can use either the command-line interface (CLI) or an Integrated Development Environment (IDE) such as Visual Studio or Visual Studio Code.

**Using the CLI:**

1. Open a terminal or command prompt.
2. Navigate to the directory where you want to create your project.
3. Run the following command to create a new .NET Core console application:
   ```
   dotnet new console -n MyConsoleApp
   ```
   Replace "MyConsoleApp" with the name of your project.
4. Navigate into the newly created project directory:
   ```
   cd MyConsoleApp
   ```
5. Open the project in your preferred text editor or IDE to start coding.

**Example:**

Let's create a simple "Hello World" console application using the CLI:

1. Open a terminal.
2. Navigate to the directory where you want to create the project.
3. Run the following command:
   ```
   dotnet new console -n HelloWorldApp
   ```
   This command creates a new .NET Core console application named "HelloWorldApp."
4. Navigate into the project directory:
   ```
   cd HelloWorldApp
   ```
5. Open the project in your text editor or IDE.
6. Open the "Program.cs" file, which contains the code for the console application.
7. Replace the contents of "Program.cs" with the following code:
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
8. Save the file and close the text editor or IDE.
9. In the terminal, run the following command to build and run the application:
   ```
   dotnet run
   ```
   You should see the output "Hello, World!" printed to the console.

**Using an IDE:**

If you prefer using an IDE, you can create a .NET Core project using Visual Studio or Visual Studio Code:

1. Open Visual Studio or Visual Studio Code.
2. Create a new project and choose ".NET Core" as the project type.
3. Select the appropriate project template (e.g., console application).
4. Provide a name and location for your project.
5. Click "Create" to generate the project files.
6. Open the generated project files in the IDE's editor.
7. Write your code and build/run the application as needed.

By following these steps, you can create a basic .NET Core application using either the CLI or your preferred IDE.