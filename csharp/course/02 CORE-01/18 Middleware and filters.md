In ASP.NET Core, middleware and filters are crucial components for handling HTTP requests and responses. They help manage cross-cutting concerns such as authentication, logging, error handling, and request validation. Here's a detailed overview of middleware and filters in Web API using C#.

### Middleware

Middleware are components that form a pipeline to handle HTTP requests and responses. Each middleware component can either pass the request to the next component or handle it directly.

#### Creating Middleware

1. **Custom Middleware**:
   Create a custom middleware by defining a class with an `Invoke` or `InvokeAsync` method.

   ```csharp
   public class CustomMiddleware
   {
       private readonly RequestDelegate _next;

       public CustomMiddleware(RequestDelegate next)
       {
           _next = next;
       }

       public async Task InvokeAsync(HttpContext context)
       {
           // Do something before the next middleware/component
           Console.WriteLine("Handling request: " + context.Request.Path);

           await _next(context);  // Call the next middleware

           // Do something after the next middleware/component
           Console.WriteLine("Finished handling request.");
       }
   }
   ```

2. **Register Middleware**:
   Register your middleware in the `Configure` method of the `Startup` class.

   ```csharp
   public class Startup
   {
       public void Configure(IApplicationBuilder app, IHostingEnvironment env)
       {
           app.UseMiddleware<CustomMiddleware>();

           app.UseRouting();
           app.UseEndpoints(endpoints =>
           {
               endpoints.MapControllers();
           });
       }
   }
   ```

#### Built-in Middleware

ASP.NET Core provides several built-in middleware components:

- **Authentication Middleware**: `app.UseAuthentication()`
- **Authorization Middleware**: `app.UseAuthorization()`
- **Static Files Middleware**: `app.UseStaticFiles()`
- **Routing Middleware**: `app.UseRouting()`
- **Endpoints Middleware**: `app.UseEndpoints()`

### Filters

Filters in ASP.NET Core are used to execute code before or after specific stages in the request processing pipeline. They are often used in MVC applications and Web APIs for handling concerns such as authorization, caching, and logging.

#### Types of Filters

1. **Authorization Filters**: Run before the request is authenticated.
2. **Resource Filters**: Run after authorization but before model binding.
3. **Action Filters**: Run before and after the action method execution.
4. **Exception Filters**: Run after an exception is thrown by an action.
5. **Result Filters**: Run before and after the result execution.

#### Creating Filters

1. **Custom Action Filter**:
   Implement the `IActionFilter` or `IAsyncActionFilter` interface.

   ```csharp
   public class CustomActionFilter : IActionFilter
   {
       public void OnActionExecuting(ActionExecutingContext context)
       {
           // Code to execute before the action
           Console.WriteLine("Before action execution");
       }

       public void OnActionExecuted(ActionExecutedContext context)
       {
           // Code to execute after the action
           Console.WriteLine("After action execution");
       }
   }
   ```

2. **Register Filters**:
   Register your filter globally in the `Startup` class or locally on a specific controller or action.

   ```csharp
   public class Startup
   {
       public void ConfigureServices(IServiceCollection services)
       {
           services.AddControllers(config =>
           {
               config.Filters.Add<CustomActionFilter>();  // Register globally
           });
       }
   }
   ```

   Alternatively, apply the filter to a specific controller or action:

   ```csharp
   [ServiceFilter(typeof(CustomActionFilter))]
   public class SampleController : ControllerBase
   {
       public IActionResult Index()
       {
           return Ok("Hello World");
       }
   }
   ```

#### Built-in Filters

ASP.NET Core includes several built-in filters such as:

- **[Authorize]**: Authorizes a user.
- **[ResponseCache]**: Caches HTTP responses.
- **[ValidateAntiForgeryToken]**: Validates anti-forgery tokens.

### Summary

Middleware and filters are powerful tools in ASP.NET Core for managing the HTTP request pipeline and handling cross-cutting concerns. Middleware operates at a lower level and is ideal for global request processing logic, while filters provide fine-grained control over specific stages of request handling in MVC and Web API applications. By using these components effectively, you can create robust, maintainable, and secure web applications.