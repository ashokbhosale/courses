Serialization and deserialization are processes used to convert data from one format (such as objects in memory) to another format (such as XML or JSON) and vice versa. In C# .NET Core, you can use built-in libraries to perform serialization and deserialization of objects to XML or JSON formats. Here's an overview of serialization and deserialization in C# .NET Core for XML and JSON:

1. **Serialization**:
   - Serialization is the process of converting objects in memory to a format that can be easily stored, transmitted, or persisted.
   - In C# .NET Core, you can use attributes such as `[Serializable]` or `[DataContract]` to mark classes for serialization.
   - For XML serialization, you can use the `System.Xml.Serialization.XmlSerializer` class.
   - For JSON serialization, you can use the `System.Text.Json.JsonSerializer` class or Newtonsoft.Json (JSON.NET) library.

Example of XML serialization:

```csharp
using System;
using System.IO;
using System.Xml.Serialization;

// Sample class for serialization
[Serializable]
public class Person
{
    public string Name { get; set; }
    public int Age { get; set; }
}

class Program
{
    static void Main()
    {
        Person person = new Person { Name = "John", Age = 30 };

        // Serialize object to XML
        XmlSerializer serializer = new XmlSerializer(typeof(Person));
        using (StreamWriter writer = new StreamWriter("person.xml"))
        {
            serializer.Serialize(writer, person);
        }
    }
}
```

Example of JSON serialization using Newtonsoft.Json (JSON.NET):

```csharp
using System;
using Newtonsoft.Json;

// Sample class for serialization
public class Person
{
    public string Name { get; set; }
    public int Age { get; set; }
}

class Program
{
    static void Main()
    {
        Person person = new Person { Name = "John", Age = 30 };

        // Serialize object to JSON using JSON.NET
        string json = JsonConvert.SerializeObject(person);
        Console.WriteLine(json);
    }
}
```

2. **Deserialization**:
   - Deserialization is the process of converting data in a serialized format (such as XML or JSON) back into objects in memory.
   - In C# .NET Core, you can use the same libraries and classes used for serialization to perform deserialization.
   - For XML deserialization, you can use the `System.Xml.Serialization.XmlSerializer` class.
   - For JSON deserialization, you can use the `System.Text.Json.JsonSerializer` class or Newtonsoft.Json (JSON.NET) library.

Example of XML deserialization:

```csharp
using System;
using System.IO;
using System.Xml.Serialization;

class Program
{
    static void Main()
    {
        // Deserialize XML to object
        XmlSerializer serializer = new XmlSerializer(typeof(Person));
        using (StreamReader reader = new StreamReader("person.xml"))
        {
            Person person = (Person)serializer.Deserialize(reader);
            Console.WriteLine($"Name: {person.Name}, Age: {person.Age}");
        }
    }
}
```

Example of JSON deserialization using Newtonsoft.Json (JSON.NET):

```csharp
using System;
using Newtonsoft.Json;

class Program
{
    static void Main()
    {
        string json = "{\"Name\":\"John\",\"Age\":30}";

        // Deserialize JSON to object using JSON.NET
        Person person = JsonConvert.DeserializeObject<Person>(json);
        Console.WriteLine($"Name: {person.Name}, Age: {person.Age}");
    }
}
```

Serialization and deserialization are essential for working with data interchange formats like XML and JSON in C# .NET Core applications. They enable communication between different systems, persistence of data, and interoperability between applications.