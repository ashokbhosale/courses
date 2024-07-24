### Memento Pattern

#### Intent and Motivation:
The Memento pattern is a behavioral design pattern that allows you to capture an object's internal state at a specific point in time and later restore it to that state, without exposing its internal structure. It enables you to implement undo mechanisms, checkpoints, or snapshots for objects, providing a way to revert them to previous states. The main intent of the Memento pattern is to provide a mechanism for capturing and restoring an object's internal state while maintaining encapsulation and without violating the object's interface.

The motivation behind the Memento pattern is to address the need to implement undo functionality or save and restore states in objects without tightly coupling the state management logic with the object's implementation. By separating the responsibility of state capture and restoration into separate objects (the memento and caretaker, respectively), the pattern promotes encapsulation, modularity, and flexibility in object-oriented designs.

#### Capturing and Restoring an Object's Internal State:
In the Memento pattern, there are several key components:

- **Originator**: Represents the object whose state needs to be saved and restored. The originator creates memento objects to capture its internal state and uses mementos to restore its state to previous snapshots.

- **Memento**: Represents the snapshot of the originator's internal state at a specific point in time. The memento provides methods for retrieving and setting the originator's state, but it does not expose the state's internal structure.

- **Caretaker**: Manages the memento objects and is responsible for storing and restoring the originator's state. The caretaker keeps a history of mementos and provides methods for saving and restoring the originator's state.

#### Implementation Techniques:
To implement the Memento pattern in .NET Core C#, you can follow these techniques:

1. **Memento Interface or Abstract Class**: Define a memento interface or abstract class that declares methods for getting and setting the originator's state. The memento should encapsulate the state without exposing its internal details.

2. **Concrete Memento**: Implement a concrete memento class that stores the originator's state at a specific point in time. The concrete memento provides methods for retrieving and setting the state.

3. **Originator**: Define an originator class that represents the object whose state needs to be saved and restored. The originator creates memento objects to capture its state and uses mementos to restore its state.

4. **Caretaker**: Implement a caretaker class that manages the memento objects and stores them in a history. The caretaker provides methods for saving and restoring the originator's state using mementos.

#### Use Cases and Examples:
The Memento pattern is suitable for scenarios where you need to implement undo functionality, checkpoints, or snapshots for objects, without tightly coupling the state management logic with the object's implementation. Some common use cases include:

- **Text Editors**: Implementing undo functionality in text editors, where users can revert changes to previous states.

- **Drawing Applications**: Providing undo functionality in drawing applications, where users can revert changes to previous drawings or modifications.

- **Transaction Management**: Implementing checkpoints or snapshots in transactional systems, where users can roll back changes to previous states in case of errors.

Example:
```csharp
using System;

// Memento interface
public interface IMemento
{
    string GetState();
}

// Concrete memento
public class ConcreteMemento : IMemento
{
    private readonly string _state;

    public ConcreteMemento(string state)
    {
        _state = state;
    }

    public string GetState()
    {
        return _state;
    }
}

// Originator
public class Originator
{
    private string _state;

    public void SetState(string state)
    {
        _state = state;
    }

    public IMemento CreateMemento()
    {
        return new ConcreteMemento(_state);
    }

    public void RestoreMemento(IMemento memento)
    {
        if (memento is ConcreteMemento concreteMemento)
        {
            _state = concreteMemento.GetState();
        }
    }

    public void ShowState()
    {
        Console.WriteLine($"Current state: {_state}");
    }
}

// Caretaker
public class Caretaker
{
    private IMemento _memento;

    public void SaveMemento(IMemento memento)
    {
        _memento = memento;
    }

    public IMemento GetMemento()
    {
        return _memento;
    }
}

// Client code
public class Client
{
    public void Main()
    {
        // Create originator
        var originator = new Originator();

        // Create caretaker
        var caretaker = new Caretaker();

        // Set state and save memento
        originator.SetState("State 1");
        caretaker.SaveMemento(originator.CreateMemento());

        // Change state
        originator.SetState("State 2");
        originator.ShowState();

        // Restore previous state
        originator.RestoreMemento(caretaker.GetMemento());
        originator.ShowState();
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

In this example, the Memento pattern is used to implement undo functionality for an originator object (`Originator`). The originator creates memento objects to capture its state at different points in time and uses mementos to restore its state to previous snapshots. The caretaker (`Caretaker`) manages the memento objects and stores them in a history, allowing the originator to revert changes using saved mementos. This demonstrates how the Memento pattern enables the capture and restoration of an object's internal state while maintaining encapsulation and separation of concerns.