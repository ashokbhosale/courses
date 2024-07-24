### Command Pattern

#### Intent and Motivation:
The Command pattern is a behavioral design pattern that encapsulates a request as an object, thereby allowing parameterization of clients with queues, requests, and operations. It enables the separation of the sender of a request from the object that executes the request, allowing requests to be treated as first-class objects. The main intent of the Command pattern is to decouple the sender of a request from the receiver, promoting loose coupling, extensibility, and flexibility.

The motivation behind the Command pattern is to address the issue of tight coupling between objects that send requests and objects that execute them. By encapsulating requests as objects, the Command pattern allows them to be parameterized, stored, and executed at a later time. This enables support for undoable operations, logging, queuing, and transaction management without modifying the sender or receiver of the request.

#### Decoupling Sender and Receiver:
In the Command pattern, there are four main participants:

- **Command**: Represents a request as an object, encapsulating both the action to be performed and the receiver of the action. It declares an interface or abstract class with a method for executing the command.

- **Concrete Command**: Implements the command interface and defines the specific action to be performed. It contains a reference to the receiver object that performs the action.

- **Invoker**: Requests the command to carry out an operation. It holds a reference to a command object and invokes the command when needed.

- **Receiver**: Performs the actual work associated with a command. It knows how to execute the command and implements the necessary logic.

#### Implementation Techniques:
The Command pattern can be implemented using the following techniques:

1. **Command Interface or Base Class**: Define a command interface or base class that declares a method for executing the command.

2. **Concrete Commands**: Implement concrete command classes that inherit from the command interface or base class. Each concrete command class represents a specific operation and holds a reference to the receiver object.

3. **Invoker**: Define an invoker class that holds a reference to a command object and invokes its execute method when needed. The invoker may also provide methods for setting or changing the command dynamically.

4. **Receiver**: Implement receiver classes that contain the actual implementation of the command logic. These classes know how to execute the command and perform the necessary operations.

#### Use Cases and Examples with .NET Core C#:
The Command pattern is commonly used in scenarios where you need to decouple the sender of a request from the receiver, such as:

- **Menu Systems**: Implementing menu systems in graphical user interfaces, where menu items represent commands that perform actions when clicked.
  
- **Transaction Management**: Managing transactions in database applications, where commands represent database operations (e.g., insert, update, delete) that can be undone or redone.
  
- **Remote Control Systems**: Building remote control systems for home appliances, where commands represent actions to be performed by devices (e.g., turning on/off lights, adjusting thermostat).

Example:
```csharp
using System;

// Command interface
public interface ICommand
{
    void Execute();
}

// Concrete command: Turn on light
public class TurnOnLightCommand : ICommand
{
    private readonly Light _light;

    public TurnOnLightCommand(Light light)
    {
        _light = light;
    }

    public void Execute()
    {
        _light.TurnOn();
    }
}

// Concrete command: Turn off light
public class TurnOffLightCommand : ICommand
{
    private readonly Light _light;

    public TurnOffLightCommand(Light light)
    {
        _light = light;
    }

    public void Execute()
    {
        _light.TurnOff();
    }
}

// Receiver
public class Light
{
    public void TurnOn()
    {
        Console.WriteLine("Light is on");
    }

    public void TurnOff()
    {
        Console.WriteLine("Light is off");
    }
}

// Invoker
public class RemoteControl
{
    private ICommand _command;

    public void SetCommand(ICommand command)
    {
        _command = command;
    }

    public void PressButton()
    {
        _command.Execute();
    }
}

// Client code
public class Client
{
    public void Main()
    {
        // Create receiver
        var light = new Light();

        // Create commands
        var turnOnCommand = new TurnOnLightCommand(light);
        var turnOffCommand = new TurnOffLightCommand(light);

        // Create invoker
        var remoteControl = new RemoteControl();

        // Set and press buttons
        remoteControl.SetCommand(turnOnCommand);
        remoteControl.PressButton();

        remoteControl.SetCommand(turnOffCommand);
        remoteControl.PressButton();
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

In this example, the Command pattern is used to encapsulate commands (`TurnOnLightCommand` and `TurnOffLightCommand`) as objects that represent actions to be performed by a receiver (`Light`). The `RemoteControl` class acts as the invoker that holds a reference to a command and invokes its `Execute` method when needed. Clients create commands, set them on the invoker, and press buttons to trigger the execution of commands. This decouples the sender (remote control) from the receiver (light), allowing different commands to be executed dynamically without modifying the invoker or receiver.