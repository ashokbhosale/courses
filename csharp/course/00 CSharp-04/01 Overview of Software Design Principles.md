Certainly! Design principles play a crucial role in software development as they guide developers in creating maintainable, scalable, and efficient code. Let's delve into some key design principles commonly used in .NET Core C# development:

1. **SOLID Principles:**
   - **Single Responsibility Principle (SRP):** A class should have only one reason to change. It means each class should have only one responsibility or only one job to do. This makes the class easier to understand, maintain, and test.
   - **Open/Closed Principle (OCP):** Software entities should be open for extension but closed for modification. It encourages the use of abstractions and interfaces, allowing new functionality to be added without altering existing code.
   - **Liskov Substitution Principle (LSP):** Objects of a superclass should be replaceable with objects of its subclasses without affecting the correctness of the program. In other words, derived classes should be substitutable for their base classes.
   - **Interface Segregation Principle (ISP):** Clients should not be forced to depend on interfaces they do not use. It's better to have multiple specific interfaces than a single large interface.
   - **Dependency Inversion Principle (DIP):** High-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details; details should depend on abstractions.

2. **DRY (Don't Repeat Yourself):**
   - This principle emphasizes the importance of code reusability and reducing redundancy. It suggests that every piece of knowledge or logic should have a single, unambiguous representation within a system.

3. **KISS (Keep It Simple, Stupid):**
   - Simplicity is preferred over complexity. This principle advocates for writing simple and understandable code rather than unnecessarily complex solutions. Simple code is easier to understand, maintain, and debug.

4. **YAGNI (You Ain't Gonna Need It):**
   - This principle advises against adding functionality until it is deemed necessary. It encourages developers to avoid over-engineering by only implementing features when they are actually needed. This helps in preventing unnecessary complexity and reduces the chances of introducing bugs.

In .NET Core C# development, these principles are often applied through various techniques such as object-oriented programming, design patterns (like Factory, Strategy, Observer, etc.), and architectural patterns (like MVC, MVVM, etc.). Adhering to these principles leads to code that is easier to understand, maintain, and extend, ultimately resulting in higher-quality software.