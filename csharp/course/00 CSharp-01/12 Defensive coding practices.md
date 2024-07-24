Defensive coding practices aim to make your code more resilient to unexpected inputs, states, and failures. Here are some defensive coding practices you can apply in .NET Core C#:

### Input Validation

1. **Validate Method Arguments**: Check the validity of method arguments to ensure they meet expected conditions.
   
   ```csharp
   public void DoSomething(int value)
   {
       if (value < 0)
       {
           throw new ArgumentException("Value must be non-negative", nameof(value));
       }
       // Proceed with the method logic
   }
   ```

2. **Use Built-in Validation Attributes**: Utilize built-in validation attributes for model properties in ASP.NET Core applications.
   
   ```csharp
   public class User
   {
       [Required]
       public string Name { get; set; }
   }
   ```

### Error Handling

3. **Handle Exceptions**: Properly handle exceptions and provide meaningful error messages to users or logs.
   
   ```csharp
   try
   {
       // Code that might throw an exception
   }
   catch (Exception ex)
   {
       // Log or handle the exception appropriately
   }
   ```

4. **Graceful Degradation**: Design your code to gracefully handle failures and degrade functionality instead of crashing.
   
   ```csharp
   try
   {
       // Code that might fail
   }
   catch (Exception ex)
   {
       // Provide alternative behavior or notify the user
   }
   ```

### Code Structure

5. **Use Interfaces**: Use interfaces to define contracts and promote loose coupling between components.
   
   ```csharp
   public interface IService
   {
       void DoWork();
   }

   public class MyService : IService
   {
       public void DoWork()
       {
           // Implementation
       }
   }
   ```

6. **Dependency Injection**: Utilize dependency injection to inject dependencies into components, improving testability and flexibility.
   
   ```csharp
   public class MyService
   {
       private readonly ILogger<MyService> _logger;

       public MyService(ILogger<MyService> logger)
       {
           _logger = logger;
       }
   }
   ```

### Resource Management

7. **Dispose Resources**: Dispose of resources such as database connections, file handles, or network connections properly.
   
   ```csharp
   using (var connection = new SqlConnection(connectionString))
   {
       // Use the connection
   }
   ```

8. **Using Statement**: Use the `using` statement for disposable objects to ensure they are properly disposed of when no longer needed.
   
   ```csharp
   using (var fileStream = new FileStream("file.txt", FileMode.Open))
   {
       // Use the file stream
   }
   ```

### Testing

9. **Unit Tests**: Write comprehensive unit tests to verify the behavior of your code under different scenarios.
   
   ```csharp
   [Test]
   public void DoSomething_WithNegativeValue_ThrowsException()
   {
       var myClass = new MyClass();

       Assert.Throws<ArgumentException>(() => myClass.DoSomething(-1));
   }
   ```

10. **Integration Tests**: Conduct integration tests to ensure that different components of your application work together as expected.

By applying these defensive coding practices, you can write more robust, reliable, and maintainable .NET Core C# code. Remember that defensive coding is about anticipating and handling potential problems before they occur, improving the resilience of your software. Let me know if you need further clarification or more examples!