Event handling in .NET Core involves subscribing to and handling events raised by objects. Events are a way for objects to communicate when something notable happens, such as a button being clicked, a timer elapsing, or data being received. Here's how event handling works in .NET Core:

1. **Define an Event**:
   - An event is declared in a class using the `event` keyword followed by the delegate type that defines the event handler signature.
   - Events are typically declared as public to allow other classes to subscribe to them.

Example:

```csharp
public class Button
{
    public event EventHandler Click;

    // Method to raise the Click event
    protected virtual void OnClick(EventArgs e)
    {
        Click?.Invoke(this, e);
    }
}
```

2. **Subscribe to an Event**:
   - To handle an event, you subscribe to it by attaching a method (event handler) to the event.
   - You do this by using the `+=` operator to add the event handler method to the event.

Example:

```csharp
Button button = new Button();
button.Click += Button_Click;

private void Button_Click(object sender, EventArgs e)
{
    // Handle the button click event
    Console.WriteLine("Button clicked!");
}
```

3. **Unsubscribe from an Event**:
   - It's important to unsubscribe from events when they are no longer needed to prevent memory leaks.
   - Use the `-=` operator to remove an event handler from an event.

Example:

```csharp
button.Click -= Button_Click;
```

4. **Raise an Event**:
   - When the conditions for the event occur, the object raising the event calls the event's invocation list, executing all attached event handlers.

Example:

```csharp
// Inside the Button class
protected void OnClick(EventArgs e)
{
    Click?.Invoke(this, e);
}
```

5. **Common Event Patterns**:
   - Events typically use the `EventHandler` delegate or its generic counterpart `EventHandler<TEventArgs>`.
   - The event handler method should follow the pattern `void EventHandlerName(object sender, EventArgs e)`.

Event handling is a fundamental concept in .NET Core and is used extensively in graphical user interfaces, asynchronous programming, and other scenarios where objects need to communicate with each other. Understanding how to define, subscribe to, and handle events is essential for developing robust and responsive applications.