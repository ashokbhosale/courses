**Introduction to ASP.NET Core and its Architecture:**

ASP.NET Core is an open-source, cross-platform framework for building modern web applications and services. It's designed to be modular, lightweight, and highly scalable. ASP.NET Core supports MVC (Model-View-Controller) and Web API patterns for building web applications and services.

**Setting up an ASP.NET Core Project:**

You can set up an ASP.NET Core project using the .NET Core CLI or Visual Studio IDE. Here's how to create a new ASP.NET Core project using the CLI:

```
dotnet new web -n MyAspNetCoreApp
cd MyAspNetCoreApp
```

This command creates a new ASP.NET Core web application project named "MyAspNetCoreApp".

**Routing and MVC Pattern:**

Routing in ASP.NET Core maps incoming HTTP requests to controller actions based on URL patterns. The MVC pattern separates the application into models (data), views (UI), and controllers (logic). Routes define how URLs are mapped to controller actions.

```csharp
// Startup.cs
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapControllerRoute(
            name: "default",
            pattern: "{controller=Home}/{action=Index}/{id?}");
    });
}
```

**Middleware Pipeline and Request Processing:**

ASP.NET Core uses a middleware pipeline to process incoming HTTP requests. Each middleware component in the pipeline performs a specific task, such as logging, authentication, or routing. Middleware is configured in the `Startup.cs` file.

```csharp
// Startup.cs
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    app.UseExceptionHandler("/Home/Error");
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
```

**Working with Controllers and Views:**

Controllers in ASP.NET Core handle incoming HTTP requests, process data, and return responses. Views are used to generate HTML output that is sent back to the client. Controllers and views work together to handle user interactions and display content.

```csharp
// HomeController.cs
public class HomeController : Controller
{
    public IActionResult Index()
    {
        return View();
    }
}

// Index.cshtml (View)
<h1>Welcome to MyAspNetCoreApp!</h1>
```

**Handling Form Submissions and Data Validation:**

ASP.NET Core provides model binding to map form data to controller action parameters. Data validation can be performed using data annotations or custom validation logic.

```csharp
// HomeController.cs
[HttpPost]
public IActionResult SubmitForm([FromBody] FormData formData)
{
    if (ModelState.IsValid)
    {
        // Process form data
        return RedirectToAction("Success");
    }
    else
    {
        // Return validation errors
        return View("Form", formData);
    }
}

// FormData.cs (Model)
public class FormData
{
    [Required]
    public string Name { get; set; }

    [EmailAddress]
    public string Email { get; set; }
}
```

These examples demonstrate the fundamental aspects of ASP.NET Core, including setting up a project, routing, MVC pattern, middleware pipeline, controllers, views, and handling form submissions and data validation. Understanding these concepts is essential for building modern web applications with ASP.NET Core.