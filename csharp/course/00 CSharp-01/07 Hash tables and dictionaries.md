In .NET Core (and later .NET 5+), hash tables and dictionaries are commonly implemented using the `Dictionary<TKey, TValue>` class in the `System.Collections.Generic` namespace. Here's how you can use dictionaries in C#:

### Dictionary<TKey, TValue>
A dictionary is a collection of key-value pairs where each key must be unique.

```csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        // Creating a dictionary with string keys and int values
        Dictionary<string, int> dictionary = new Dictionary<string, int>();

        // Adding key-value pairs
        dictionary["apple"] = 10;
        dictionary["banana"] = 20;
        dictionary["orange"] = 30;

        // Accessing values by key
        Console.WriteLine($"Value for 'apple': {dictionary["apple"]}"); // Output: Value for 'apple': 10

        // Checking if a key exists
        if (dictionary.ContainsKey("banana"))
        {
            Console.WriteLine("Dictionary contains 'banana' key");
        }

        // Iterating over key-value pairs
        foreach (var kvp in dictionary)
        {
            Console.WriteLine($"Key: {kvp.Key}, Value: {kvp.Value}");
        }
    }
}
```

### Hashtable
Hashtable is an older data structure in .NET Framework, but you can still use it. It's a collection of key-value pairs where the keys are hashed to produce a unique integer, which is then used to look up the corresponding value.

```csharp
using System;
using System.Collections;

class Program
{
    static void Main()
    {
        // Creating a hashtable
        Hashtable hashtable = new Hashtable();

        // Adding key-value pairs
        hashtable["apple"] = 10;
        hashtable["banana"] = 20;
        hashtable["orange"] = 30;

        // Accessing values by key
        Console.WriteLine($"Value for 'apple': {hashtable["apple"]}"); // Output: Value for 'apple': 10

        // Checking if a key exists
        if (hashtable.ContainsKey("banana"))
        {
            Console.WriteLine("Hashtable contains 'banana' key");
        }

        // Iterating over key-value pairs
        foreach (DictionaryEntry entry in hashtable)
        {
            Console.WriteLine($"Key: {entry.Key}, Value: {entry.Value}");
        }
    }
}
```

In .NET Core and newer versions, it's recommended to use `Dictionary<TKey, TValue>` over `Hashtable` due to better type safety and performance. However, `Hashtable` might still be useful in specific scenarios or when dealing with legacy code.

These examples demonstrate how to use hash tables and dictionaries in .NET Core C#. Let me know if you need further clarification or more examples!