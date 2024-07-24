The SOLID principles are a set of five design principles that help developers design more maintainable, flexible, and scalable object-oriented software. They are guidelines aimed at producing clean, modular code that is easier to understand, extend, and maintain over time. Let's explore each principle with examples in C# .NET Core:

1. **Single Responsibility Principle (SRP)**:
   This principle states that a class should have only one reason to change, meaning that a class should have only one responsibility.
   
   Example:
   ```csharp
   // Bad example: A class with multiple responsibilities
   public class UserService
   {
       public void RegisterUser(User user)
       {
           // Register user logic
       }
       
       public void SendEmailConfirmation(User user)
       {
           // Send email logic
       }
       
       public void LogRegistrationActivity(User user)
       {
           // Logging logic
       }
   }
   
   // Good example: Separating responsibilities into different classes
   public class UserService
   {
       public void RegisterUser(User user)
       {
           // Register user logic
       }
   }
   
   public class EmailService
   {
       public void SendEmailConfirmation(User user)
       {
           // Send email logic
       }
   }
   
   public class Logger
   {
       public void LogActivity(string message)
       {
           // Logging logic
       }
   }
   ```

2. **Open/Closed Principle (OCP)**:
   This principle states that classes should be open for extension but closed for modification. It encourages the use of abstraction to allow behavior to be extended without modifying existing code.
   
   Example:
   ```csharp
   // Bad example: Modifying existing code for new requirements
   public class Shape
   {
       public virtual double Area() { /* Calculate area */ }
   }
   
   public class Circle : Shape
   {
       public override double Area() { /* Calculate area */ }
   }
   
   public class Square : Shape
   {
       public override double Area() { /* Calculate area */ }
   }
   
   // Good example: Using abstraction to support new shapes without modifying existing code
   public abstract class Shape
   {
       public abstract double Area();
   }
   
   public class Circle : Shape
   {
       public override double Area() { /* Calculate area */ }
   }
   
   public class Square : Shape
   {
       public override double Area() { /* Calculate area */ }
   }
   
   public class Triangle : Shape
   {
       public override double Area() { /* Calculate area */ }
   }
   ```

3. **Liskov Substitution Principle (LSP)**:
   This principle states that objects of a superclass should be replaceable with objects of its subclass without affecting the functionality of the program. In other words, derived classes must be substitutable for their base classes.
   
   Example:
   ```csharp
   // Bad example: Violating LSP
   public class Rectangle
   {
       public virtual int Width { get; set; }
       public virtual int Height { get; set; }
   }
   
   public class Square : Rectangle
   {
       public override int Width
       {
           set { base.Width = base.Height = value; }
       }
       
       public override int Height
       {
           set { base.Width = base.Height = value; }
       }
   }
   
   // Good example: Ensuring LSP compliance
   public class Shape
   {
       public virtual double Area() { /* Calculate area */ }
   }
   
   public class Rectangle : Shape
   {
       public int Width { get; set; }
       public int Height { get; set; }
       
       public override double Area() { /* Calculate area */ }
   }
   
   public class Square : Shape
   {
       public int SideLength { get; set; }
       
       public override double Area() { /* Calculate area */ }
   }
   ```

4. **Interface Segregation Principle (ISP)**:
   This principle states that clients should not be forced to depend on interfaces they do not use. It encourages the use of smaller, cohesive interfaces instead of large, monolithic ones.
   
   Example:
   ```csharp
   // Bad example: Large interface with unnecessary methods
   public interface IWorker
   {
       void Work();
       void Eat();
       void Sleep();
   }
   
   // Good example: Smaller, focused interfaces
   public interface IWorker
   {
       void Work();
   }
   
   public interface IEater
   {
       void Eat();
   }
   
   public interface ISleeper
   {
       void Sleep();
   }
   ```

5. **Dependency Inversion Principle (DIP)**:
   This principle states that high-level modules should not depend on low-level modules; both should depend on abstractions. Additionally, abstractions should not depend on details; details should depend on abstractions. It promotes loose coupling between components.
   
   Example:
   ```csharp
   // Bad example: High-level module directly depends on low-level module
   public class Logger
   {
       public void Log(string message)
       {
           // Logging logic
       }
   }
   
   public class UserService
   {
       private readonly Logger _logger;
       
       public UserService()
       {
           _logger = new Logger();
       }
       
       public void RegisterUser(User user)
       {
           // Register user logic
           _logger.Log("User registered: " + user.Name);
       }
   }
   
   // Good example: Abstraction introduced to decouple modules
   public interface ILogger
   {
       void Log(string message);
   }
   
   public class Logger : ILogger
   {
       public void Log(string message)
       {
           // Logging logic
       }
   }
   
   public class UserService
   {
       private readonly ILogger _logger;
       
       public UserService(ILogger logger)
       {
           _logger = logger;
       }
       
       public void RegisterUser(User user)
       {
           // Register user logic
           _logger.Log("User registered: " + user.Name);
       }
   }
   ```

By following the SOLID principles, developers can create more modular, flexible, and maintainable C# .NET Core applications that are easier to understand, extend, and refactor as requirements change.