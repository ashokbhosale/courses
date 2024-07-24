Creating custom middleware components in ASP.NET Core allows you to handle HTTP requests and responses in a flexible and reusable manner. Middleware sits between the client and the server, allowing you to execute logic before and after the request reaches your application's endpoints. Let's create a custom middleware component in a .NET Core application:

```csharp
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Http;
using System;
using System.Threading.Tasks;

public class CustomMiddleware
{
    private readonly RequestDelegate _next;

    public CustomMiddleware(RequestDelegate next)
    {
        _next = next;
    }

    public async Task InvokeAsync(HttpContext context)
    {
        // Logic to be executed before passing the request to the next middleware
        Console.WriteLine("Executing custom middleware before request processing.");

        // Call the next middleware in the pipeline
        await _next(context);

        // Logic to be executed after the request has been processed by subsequent middleware
        Console.WriteLine("Executing custom middleware after request processing.");
    }
}

public static class CustomMiddlewareExtensions
{
    public static IApplicationBuilder UseCustomMiddleware(this IApplicationBuilder builder)
    {
        return builder.UseMiddleware<CustomMiddleware>();
    }
}
```

In this example:
- We create a `CustomMiddleware` class with a constructor that takes a `RequestDelegate`, which represents the next middleware in the pipeline.
- We implement the `InvokeAsync` method, where we can execute logic before and after the request is processed. Inside this method, we call `_next(context)` to pass the request to the next middleware in the pipeline.
- We define an extension method `UseCustomMiddleware` that adds our custom middleware to the ASP.NET Core middleware pipeline.

Now, let's use our custom middleware in the `Startup.cs` class:

```csharp
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Hosting;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;

public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddControllersWithViews();
    }

    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
        else
        {
            app.UseExceptionHandler("/Home/Error");
            app.UseHsts();
        }

        app.UseHttpsRedirection();
        app.UseStaticFiles();

        app.UseRouting();

        // Use our custom middleware
        app.UseCustomMiddleware();

        app.UseAuthorization();

        app.UseEndpoints(endpoints =>
        {
            endpoints.MapControllerRoute(
                name: "default",
                pattern: "{controller=Home}/{action=Index}/{id?}");
        });
    }
}
```

Now, our custom middleware will be executed for every HTTP request processed by the ASP.NET Core application. You can add any custom logic you need inside the `CustomMiddleware` class to handle specific tasks in the request pipeline.