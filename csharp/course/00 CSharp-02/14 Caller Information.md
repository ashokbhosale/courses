Caller Information attributes in .NET Core C# provide contextual information about the caller of a method or property. They are useful for logging, debugging, and tracing purposes, allowing you to access information about the caller's source code location. Here's how you can use Caller Information attributes in .NET Core C#:

### 1. `CallerMemberName` Attribute:

The `CallerMemberName` attribute allows you to obtain the name of the calling member (method or property) at compile time.

```csharp
public void Log(string message, [CallerMemberName] string callerName = "")
{
    Console.WriteLine($"[{callerName}]: {message}");
}

// Usage
Log("Information message"); // Caller name will be obtained automatically
```

### 2. `CallerFilePath` Attribute:

The `CallerFilePath` attribute allows you to obtain the full path of the source file that contains the caller at compile time.

```csharp
public void Log(string message, [CallerFilePath] string callerFilePath = "")
{
    Console.WriteLine($"[{callerFilePath}]: {message}");
}

// Usage
Log("Information message"); // Caller file path will be obtained automatically
```

### 3. `CallerLineNumber` Attribute:

The `CallerLineNumber` attribute allows you to obtain the line number in the source file from which the method or property was called at compile time.

```csharp
public void Log(string message, [CallerLineNumber] int callerLineNumber = 0)
{
    Console.WriteLine($"Line {callerLineNumber}: {message}");
}

// Usage
Log("Information message"); // Caller line number will be obtained automatically
```

### 4. Caller Information Attributes Summary:

- `CallerMemberName`: Retrieves the name of the calling member.
- `CallerFilePath`: Retrieves the full path of the source file containing the caller.
- `CallerLineNumber`: Retrieves the line number in the source file from which the method or property was called.

### 5. Usage Considerations:

- Caller Information attributes are resolved at compile time, so they provide information about the caller's location at compile time, not runtime.
- They can be useful for logging, tracing, and debugging purposes to provide contextual information about method calls.

### Summary:

Caller Information attributes in .NET Core C# provide contextual information about the caller's source code location. By using Caller Information attributes, you can enhance logging, tracing, and debugging capabilities in your .NET Core applications. Let me know if you need further assistance or examples!