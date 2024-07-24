**Definition and Purpose of SRP:**

The Single Responsibility Principle (SRP) is one of the SOLID principles in object-oriented programming. It states that a class should have only one reason to change, meaning it should have only one responsibility. The purpose of SRP is to improve code maintainability, readability, and reusability by keeping classes focused on a single task or responsibility.

**Examples of Violations and Adherence to SRP:**

**Violation of SRP:**

Consider a .NET Core C# example where we have a `User` class that not only represents user data but also handles authentication logic:

```csharp
public class User
{
    public string Username { get; set; }
    public string Password { get; set; }
    
    public bool Authenticate(string enteredPassword)
    {
        // Authentication logic...
    }
    
    // Other user-related methods...
}
```

In this example, the `User` class violates SRP because it has multiple responsibilities: managing user data and handling authentication. If the authentication logic needs to be updated or changed, the `User` class will need to be modified, which breaks SRP.

**Adherence to SRP:**

To adhere to SRP, we can separate the responsibilities into different classes. Here's how we can refactor the previous example:

```csharp
public class User
{
    public string Username { get; set; }
    public string Password { get; set; }
    
    // User-related methods...
}

public class Authenticator
{
    public bool Authenticate(User user, string enteredPassword)
    {
        // Authentication logic...
    }
}
```

In this refactored version, the `User` class is responsible only for managing user data, while the `Authenticator` class is responsible for handling authentication logic. This adheres to SRP because each class has a single responsibility, and changes to one responsibility (e.g., authentication logic) do not affect the other (e.g., user data management). This improves code maintainability and makes it easier to understand and modify in the future.

Let's walk through applying the Single Responsibility Principle (SRP) in C# using .NET Core. We'll identify responsibilities within classes and methods, refactor code to adhere to SRP, and explore design patterns that support SRP, such as the Command and Strategy patterns.

**Identifying Responsibilities:**

To apply SRP effectively, we need to identify different responsibilities within our classes and methods. Responsibilities can include tasks like data management, business logic, user interface interaction, and more.

**Refactoring Code:**

Once we've identified multiple responsibilities within a class or method, we can refactor the code to separate those responsibilities into distinct classes or methods. Each class or method should have a single responsibility and should be focused on performing that responsibility effectively.

**Design Patterns Supporting SRP:**

Design patterns like Command and Strategy can help in adhering to SRP by promoting separation of concerns and enabling flexibility and extensibility in our code.

Let's illustrate these concepts with an example:

```csharp
using System;

// Original class with multiple responsibilities
public class EmailService
{
    public void SendEmail(string to, string subject, string message)
    {
        // Email sending logic
        Console.WriteLine($"Sending email to {to} with subject: {subject}, and message: {message}");
    }

    public bool ValidateEmail(string email)
    {
        // Email validation logic
        return email.Contains("@");
    }

    // Additional responsibilities could be added here
}
```

In the above code, `EmailService` class violates SRP because it has multiple responsibilities: sending emails and validating email addresses.

**Refactoring to Adhere to SRP:**

```csharp
public class EmailSender
{
    public void SendEmail(string to, string subject, string message)
    {
        // Email sending logic
        Console.WriteLine($"Sending email to {to} with subject: {subject}, and message: {message}");
    }
}

public class EmailValidator
{
    public bool ValidateEmail(string email)
    {
        // Email validation logic
        return email.Contains("@");
    }
}
```

Here, we've split the responsibilities of sending emails and validating email addresses into separate classes `EmailSender` and `EmailValidator`, adhering to SRP. Each class now has a single responsibility.

**Using Design Patterns to Support SRP:**

Let's apply the Command pattern to support SRP in our example:

```csharp
public interface ICommand
{
    void Execute();
}

public class SendEmailCommand : ICommand
{
    private readonly string _to;
    private readonly string _subject;
    private readonly string _message;

    public SendEmailCommand(string to, string subject, string message)
    {
        _to = to;
        _subject = subject;
        _message = message;
    }

    public void Execute()
    {
        // Email sending logic
        Console.WriteLine($"Sending email to {_to} with subject: {_subject}, and message: {_message}");
    }
}

public class EmailServiceInvoker
{
    private readonly ICommand _command;

    public EmailServiceInvoker(ICommand command)
    {
        _command = command;
    }

    public void ExecuteCommand()
    {
        _command.Execute();
    }
}
```

In this example, the `SendEmailCommand` class encapsulates the responsibility of sending an email, while the `EmailServiceInvoker` class acts as an invoker, separating the responsibility of command execution. This aligns with SRP by keeping each class focused on a single responsibility.

Similarly, we can apply the Strategy pattern to support SRP by encapsulating different algorithms or behaviors into separate strategy classes.

By applying SRP along with appropriate design patterns, we can create well-structured, maintainable, and extensible code in .NET Core C#.