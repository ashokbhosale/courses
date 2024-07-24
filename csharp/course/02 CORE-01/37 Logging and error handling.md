Logging and error handling are essential components of robust software applications. Let's explore how to implement logging and error handling in .NET Core C# with examples:

### Logging

1. **Using Microsoft.Extensions.Logging**
   - Add the `Microsoft.Extensions.Logging` NuGet package to your project.
   ```bash
   dotnet add package Microsoft.Extensions.Logging
   ```
   
2. **Configure Logging in Startup**
   - Configure logging services in the `ConfigureServices` method of your `Startup` class.
   ```csharp
   public void ConfigureServices(IServiceCollection services)
   {
       services.AddLogging();
       // Other service configurations
   }
   ```

3. **Inject ILogger into Classes**
   - Inject an instance of `ILogger<T>` into your classes where you want to log messages.
   ```csharp
   using Microsoft.Extensions.Logging;

   public class MyClass
   {
       private readonly ILogger<MyClass> _logger;

       public MyClass(ILogger<MyClass> logger)
       {
           _logger = logger;
       }

       public void DoSomething()
       {
           _logger.LogInformation("Doing something...");
       }
   }
   ```

4. **Log Messages**
   - Use the logger instance to log messages at different log levels (Information, Warning, Error, etc.).
   ```csharp
   _logger.LogInformation("This is an information message.");
   _logger.LogWarning("This is a warning message.");
   _logger.LogError("This is an error message: {errorMessage}", ex.Message);
   ```

### Error Handling

1. **Using Try-Catch Blocks**
   - Use try-catch blocks to catch and handle exceptions.
   ```csharp
   try
   {
       // Code that may throw an exception
   }
   catch (Exception ex)
   {
       _logger.LogError("An error occurred: {errorMessage}", ex.Message);
       // Additional error handling logic
   }
   ```

2. **Global Exception Handling Middleware**
   - Implement global exception handling middleware to catch unhandled exceptions and log them.
   ```csharp
   public void Configure(IApplicationBuilder app, IWebHostEnvironment env, ILogger<Startup> logger)
   {
       if (env.IsDevelopment())
       {
           app.UseDeveloperExceptionPage();
       }
       else
       {
           app.UseExceptionHandler("/Error");
           app.UseHsts();
       }

       app.UseHttpsRedirection();
       app.UseStaticFiles();
       app.UseRouting();
       // Other middleware configurations

       app.UseEndpoints(endpoints =>
       {
           endpoints.MapControllers();
           // Other endpoint mappings
       });

       app.UseExceptionHandler(errorApp =>
       {
           errorApp.Run(async context =>
           {
               context.Response.StatusCode = (int)HttpStatusCode.InternalServerError;
               context.Response.ContentType = "text/plain";

               var exceptionHandlerPathFeature = context.Features.Get<IExceptionHandlerPathFeature>();
               logger.LogError($"The path {exceptionHandlerPathFeature.Path} threw an exception: {exceptionHandlerPathFeature.Error}");

               await context.Response.WriteAsync("An unexpected error occurred. Please try again later.");
           });
       });
   }
   ```

3. **Custom Exception Handling Middleware**
   - Implement custom middleware to handle specific types of exceptions and log them.
   ```csharp
   public class CustomExceptionMiddleware
   {
       private readonly RequestDelegate _next;
       private readonly ILogger<CustomExceptionMiddleware> _logger;

       public CustomExceptionMiddleware(RequestDelegate next, ILogger<CustomExceptionMiddleware> logger)
       {
           _next = next;
           _logger = logger;
       }

       public async Task Invoke(HttpContext context)
       {
           try
           {
               await _next(context);
           }
           catch (Exception ex)
           {
               _logger.LogError($"An error occurred: {ex.Message}");
               context.Response.StatusCode = (int)HttpStatusCode.InternalServerError;
               context.Response.ContentType = "text/plain";
               await context.Response.WriteAsync("An unexpected error occurred. Please try again later.");
           }
       }
   }

   // In Startup.cs
   public void Configure(IApplicationBuilder app, ILogger<Startup> logger)
   {
       app.UseMiddleware<CustomExceptionMiddleware>();
       // Other middleware configurations
   }
   ```

By implementing logging and error handling in your .NET Core C# application, you can effectively monitor and manage application behavior, diagnose issues, and provide a better user experience.