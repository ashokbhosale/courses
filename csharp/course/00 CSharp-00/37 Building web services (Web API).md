To build a Web API with .NET Core C#, you'll follow these general steps:

1. **Create a New Web API Project**:
   - Use Visual Studio or the .NET CLI to create a new Web API project.
   - For the .NET CLI, run:
     ```
     dotnet new webapi -n MyWebApi
     ```
   This creates a new Web API project named "MyWebApi".

2. **Define Models**:
   - Define the data models that represent the entities your API will work with.
   - These models define the structure of the data that your API will send and receive.

3. **Create Controllers**:
   - Controllers handle incoming HTTP requests and return appropriate responses.
   - Each controller typically corresponds to a resource or entity in your application.
   - Use attributes like `[HttpGet]`, `[HttpPost]`, `[HttpPut]`, `[HttpDelete]` to define the HTTP methods and routes for controller actions.

4. **Implement Action Methods**:
   - Inside your controllers, implement action methods to handle specific HTTP requests.
   - These methods typically perform CRUD operations (Create, Read, Update, Delete) on your data models.

5. **Use Dependency Injection (DI)**:
   - Register any services your controllers need with the ASP.NET Core DI container.
   - Services might include repositories, data access layers, or other components.

6. **Configure Routing**:
   - Define URL routes for your API's controllers and actions.
   - You can use convention-based routing or attribute routing to specify routes.

7. **Handle Requests and Responses**:
   - Use action method return types like `ActionResult<T>` to return HTTP responses with status codes and content.
   - Return different types of results like `Ok`, `NotFound`, `BadRequest`, etc., based on the outcome of the request.

8. **Configure Middleware**:
   - Configure any middleware your application needs in the `Startup.cs` file.
   - Middleware can handle tasks like logging, exception handling, authentication, and authorization.

9. **Test Your API**:
   - Use tools like Postman, Swagger, or curl to test your API endpoints.
   - Test various scenarios including success cases, error handling, input validation, etc.

10. **Document Your API**:
    - Optionally, document your API using tools like Swagger/OpenAPI to provide documentation for consumers.

11. **Deploy Your API**:
    - Once your API is ready, deploy it to a hosting environment such as Azure, AWS, or a self-hosted server.

Following these steps will help you create a robust Web API with .NET Core C#. Make sure to adhere to best practices for security, performance, and maintainability throughout the development process.