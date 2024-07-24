Handling HTTP requests and responses in ASP.NET Core involves creating controllers to handle incoming requests and generating responses. Here's an example of how to handle HTTP requests and responses in .NET Core C#:

1. **Creating a Controller**:
   - Create a new controller class that inherits from `Controller` or `ControllerBase` depending on your needs.
   - Example of a simple controller in C#:
     ```csharp
     using Microsoft.AspNetCore.Mvc;

     [Route("api/[controller]")]
     [ApiController]
     public class HelloController : ControllerBase
     {
         [HttpGet]
         public IActionResult Get()
         {
             return Ok("Hello, world!");
         }
     }
     ```
   - In this example, the `HelloController` class defines an action method `Get()` that returns a simple "Hello, world!" message in response to a GET request.

2. **Routing Requests**:
   - Use attributes like `[HttpGet]`, `[HttpPost]`, `[HttpPut]`, `[HttpDelete]`, etc., to specify the HTTP methods that each action method handles.
   - Decorate the controller class or individual action methods with the `[Route]` attribute to define the URL route template for the controller or action.
   - Example of routing HTTP requests in C#:
     ```csharp
     [HttpGet("greet")]
     public IActionResult Greet()
     {
         return Ok("Greetings from the HelloController!");
     }
     ```
   - This action method handles GET requests to the route "/api/hello/greet" and returns a greeting message.

3. **Accessing Request Data**:
   - Use method parameters annotated with attributes like `[FromQuery]`, `[FromRoute]`, `[FromBody]`, etc., to bind request data to method parameters.
   - Example of accessing query string parameters in C#:
     ```csharp
     [HttpGet("user")]
     public IActionResult GetUser([FromQuery] string name)
     {
         return Ok($"Hello, {name}!");
     }
     ```
   - This action method handles GET requests to the route "/api/hello/user" with a query string parameter "name" and returns a personalized greeting.

4. **Returning Responses**:
   - Use `ActionResult<T>` or `IActionResult` to return different types of responses such as JSON data, status codes, or custom objects.
   - Example of returning JSON data in C#:
     ```csharp
     [HttpGet("json")]
     public IActionResult GetJson()
     {
         var data = new { message = "Hello, JSON!" };
         return Ok(data);
     }
     ```
   - This action method handles GET requests to the route "/api/hello/json" and returns JSON data containing a greeting message.

By following these examples, you can handle HTTP requests and responses effectively in ASP.NET Core using C#. You can create controllers to handle various types of requests, access request data, and return appropriate responses based on your application's requirements.