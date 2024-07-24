Working with streams in .NET Core C# allows you to efficiently read from and write to data sources, such as files, network connections, memory, and more. Streams provide a common interface for reading and writing sequential data, making it easier to work with different types of data sources. Here's an overview of working with streams in .NET Core C#:

1. **Stream Class**:
   - The `System.IO.Stream` class is an abstract base class that represents a generic stream of bytes.
   - Streams can be used for both reading and writing data, and they provide methods and properties for performing various operations on the data.
   - Different types of streams are derived from the `Stream` class, such as `FileStream`, `MemoryStream`, `NetworkStream`, `CryptoStream`, etc.

2. **Reading from Streams**:
   - To read from a stream, you typically create an instance of a stream reader class, such as `StreamReader` or `BinaryReader`, and use its methods to read data from the stream.
   - The `Read()` method reads a specified number of bytes from the stream into a byte array or a buffer.
   - The `ReadByte()` method reads a single byte from the stream and advances the position within the stream.

Example of reading from a file stream using `StreamReader`:

```csharp
using System;
using System.IO;

class Program
{
    static void Main()
    {
        using (FileStream fs = File.OpenRead("data.txt"))
        using (StreamReader reader = new StreamReader(fs))
        {
            string line;
            while ((line = reader.ReadLine()) != null)
            {
                Console.WriteLine(line);
            }
        }
    }
}
```

3. **Writing to Streams**:
   - To write to a stream, you typically create an instance of a stream writer class, such as `StreamWriter` or `BinaryWriter`, and use its methods to write data to the stream.
   - The `Write()` method writes a specified number of bytes from a byte array or a buffer to the stream.
   - The `WriteByte()` method writes a single byte to the stream.

Example of writing to a file stream using `StreamWriter`:

```csharp
using System.IO;

class Program
{
    static void Main()
    {
        using (FileStream fs = File.Create("output.txt"))
        using (StreamWriter writer = new StreamWriter(fs))
        {
            writer.WriteLine("Hello, world!");
        }
    }
}
```

4. **Using Streams with Binary Data**:
   - Streams can also be used to work with binary data, such as reading and writing primitive data types (integers, floats, etc.), byte arrays, and serialized objects.
   - BinaryReader and BinaryWriter classes provide methods for reading and writing binary data to streams in a type-safe manner.

Working with streams in .NET Core C# allows you to efficiently read from and write to different types of data sources, making it easier to handle input/output operations in your applications. By using streams, you can achieve better performance, reduced memory usage, and improved scalability.