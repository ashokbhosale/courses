In C# .NET Core, reading and writing to files is a common task for interacting with file-based data such as text files, CSV files, XML files, JSON files, and more. Here's an overview of how to perform reading and writing operations on files:

1. **Reading from Files**:
   - Use the `System.IO.File` class to read from files in C#.
   - The `File.ReadAllText()` method reads the contents of a text file and returns it as a single string.
   - The `File.ReadAllLines()` method reads all lines of a text file into a string array, with each line as an element of the array.
   - The `File.ReadAllBytes()` method reads all bytes from a binary file and returns them as a byte array.

Example of reading from a text file:

```csharp
using System;
using System.IO;

class Program
{
    static void Main()
    {
        string path = @"C:\path\to\file.txt";

        // Read all text from the file
        string content = File.ReadAllText(path);
        Console.WriteLine(content);

        // Read all lines from the file
        string[] lines = File.ReadAllLines(path);
        foreach (string line in lines)
        {
            Console.WriteLine(line);
        }

        // Read all bytes from the file
        byte[] bytes = File.ReadAllBytes(path);
    }
}
```

2. **Writing to Files**:
   - Use the `System.IO.File` class to write to files in C#.
   - The `File.WriteAllText()` method writes a string to a text file, overwriting the file if it already exists.
   - The `File.WriteAllLines()` method writes an array of strings to a text file, with each string representing a line in the file.
   - The `File.WriteAllBytes()` method writes a byte array to a binary file.

Example of writing to a text file:

```csharp
using System.IO;

class Program
{
    static void Main()
    {
        string path = @"C:\path\to\file.txt";
        string content = "Hello, world!";

        // Write text to the file (overwrite if it already exists)
        File.WriteAllText(path, content);

        // Write lines to the file (overwrite if it already exists)
        string[] lines = { "Line 1", "Line 2", "Line 3" };
        File.WriteAllLines(path, lines);

        // Write bytes to the file (overwrite if it already exists)
        byte[] bytes = { 0x48, 0x65, 0x6C, 0x6C, 0x6F }; // ASCII bytes for "Hello"
        File.WriteAllBytes(path, bytes);
    }
}
```

3. **Handling Exceptions**:
   - When reading or writing files, it's essential to handle exceptions, such as `IOException`, `UnauthorizedAccessException`, `FileNotFoundException`, etc., that may occur due to file access issues, permissions, or file not found errors.

Reading and writing to files is a fundamental operation in C# .NET Core applications for handling data persistence, configuration, logging, and more. Using the `System.IO.File` class, you can easily perform file I/O operations in a platform-independent manner.