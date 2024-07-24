### Flyweight Pattern

#### Intent and Motivation:
The Flyweight pattern is a structural design pattern that aims to minimize memory usage or computational expenses by sharing as much as possible with similar objects. It is particularly useful when dealing with a large number of objects with similar properties, as it allows the sharing of common parts of state among multiple objects, instead of each object storing its own copy. The main intent of the Flyweight pattern is to reduce the memory footprint and improve performance by sharing intrinsic (invariant) state among multiple objects.

The motivation behind the Flyweight pattern is to address the inefficiencies that arise when dealing with a large number of fine-grained objects, especially when many of these objects share common characteristics. By separating the intrinsic (shared) state from the extrinsic (context-dependent) state and storing the intrinsic state externally, the pattern minimizes the memory overhead associated with storing redundant information. This can lead to significant savings in memory usage and processing time, especially in memory-constrained or performance-sensitive applications.

#### Sharing Objects to Support Large Numbers of Fine-grained Objects:
In the Flyweight pattern, there are two main types of state:

- **Intrinsic State**: Represents the shared (immutable) state that can be shared among multiple objects. This state is stored externally and can be accessed by flyweight objects.

- **Extrinsic State**: Represents the context-dependent (mutable) state that varies across different contexts or instances of flyweight objects. This state is passed as an argument to flyweight objects when they are used.

#### Implementation Techniques:
To implement the Flyweight pattern in .NET Core C#, you can follow these techniques:

1. **Flyweight Interface or Base Class**: Define a flyweight interface or base class that declares methods for accessing and manipulating the intrinsic state.

2. **Concrete Flyweight**: Implement concrete flyweight classes that represent individual flyweight objects. These classes store the extrinsic state as parameters and delegate operations involving intrinsic state to an external source.

3. **Flyweight Factory**: Implement a flyweight factory that manages the creation and sharing of flyweight objects. The factory maintains a pool of flyweight objects and ensures that objects are shared when requested.

4. **Client Code**: Use flyweight objects in client code by providing extrinsic state as arguments when needed. Clients interact with flyweight objects without being aware of their shared state.

#### Use Cases and Examples:
The Flyweight pattern is suitable for scenarios where a large number of fine-grained objects need to be managed efficiently, especially when many of these objects share common characteristics. Some common use cases include:

- **Text Processing**: Storing and managing characters or glyphs in a text editor efficiently, where many characters may share the same font or style information.

- **Graphic User Interfaces**: Handling graphical elements such as icons, buttons, or shapes in a user interface framework, where many instances of similar elements need to be displayed.

- **Game Development**: Managing game objects such as particles, tiles, or sprites in a game engine, where large numbers of objects with shared properties need to be rendered efficiently.

Example:
```csharp
using System;
using System.Collections.Generic;

// Flyweight interface
public interface ICharacter
{
    void Display(int size);
}

// Concrete flyweight representing a character
public class Character : ICharacter
{
    private readonly char _symbol;

    public Character(char symbol)
    {
        _symbol = symbol;
    }

    public void Display(int size)
    {
        Console.WriteLine($"Character {_symbol} displayed with size {size}");
    }
}

// Flyweight factory
public class CharacterFactory
{
    private readonly Dictionary<char, ICharacter> _characters = new Dictionary<char, ICharacter>();

    public ICharacter GetCharacter(char symbol)
    {
        if (!_characters.ContainsKey(symbol))
        {
            _characters[symbol] = new Character(symbol);
        }
        return _characters[symbol];
    }
}

// Client code
public class Client
{
    public void Main()
    {
        // Create a flyweight factory
        var factory = new CharacterFactory();

        // Use flyweight objects
        var characterA = factory.GetCharacter('A');
        var characterB = factory.GetCharacter('B');
        var characterA2 = factory.GetCharacter('A');

        characterA.Display(12);
        characterB.Display(14);
        characterA2.Display(16); // The same object as characterA

        // Extrinsic state can be passed as an argument if needed
    }
}

// Usage
public class Program
{
    public static void Main()
    {
        var client = new Client();
        client.Main();
    }
}
```

In this example, the Flyweight pattern is used to efficiently manage character objects (`Character`) in a text processing application. The `CharacterFactory` class acts as a flyweight factory that creates and shares flyweight objects based on their intrinsic state (the character symbol). Clients retrieve flyweight objects from the factory and use them to display characters with varying sizes. Since characters with the same symbol share the same intrinsic state, they can be reused, leading to memory savings and improved performance.