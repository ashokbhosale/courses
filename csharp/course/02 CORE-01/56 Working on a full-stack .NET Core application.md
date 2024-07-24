Building a full-stack .NET Core application involves developing both the backend (server-side) and the frontend (client-side) components. Let's outline a simple example of a full-stack .NET Core application using ASP.NET Core for the backend and Razor Pages for the frontend:

### 1. Backend (ASP.NET Core):

#### Example:
```csharp
// Startup.cs
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
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

        app.UseAuthorization();

        app.UseEndpoints(endpoints =>
        {
            endpoints.MapControllerRoute(
                name: "default",
                pattern: "{controller=Home}/{action=Index}/{id?}");
        });
    }
}

// HomeController.cs
public class HomeController : Controller
{
    public IActionResult Index()
    {
        return View();
    }
}
```

### 2. Frontend (Razor Pages):

#### Example:
```html
<!-- Views/Home/Index.cshtml -->
@page
@model IndexModel
@{
    ViewData["Title"] = "Home Page";
}

<div class="text-center">
    <h1 class="display-4">Welcome</h1>
    <p>Learn about .NET Core full-stack development!</p>
</div>
```

### 3. Project Structure:

Your project structure may look like this:
```
- MyFullStackApp (Solution)
    - MyFullStackApp (ASP.NET Core Web Application)
        - Controllers
            - HomeController.cs
        - Views
            - Home
                - Index.cshtml
        - wwwroot
        - Startup.cs
        - ...
    - MyFullStackApp.Tests (Unit Test Project)
    - ...
```

### 4. Running the Application:

You can run the application using the `dotnet run` command or directly from Visual Studio by pressing F5.

### Conclusion:

This is a basic example of a full-stack .NET Core application using ASP.NET Core for the backend and Razor Pages for the frontend. As you build your application, you can expand it by adding features like database access, user authentication, API endpoints, and more. Don't hesitate to explore additional frameworks and libraries within the .NET ecosystem to enhance your application's functionality and user experience.