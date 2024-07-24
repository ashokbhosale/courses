Routing and the Model-View-Controller (MVC) architecture are fundamental concepts in ASP.NET Core for handling incoming requests and generating responses. Let's explore how routing and MVC architecture work in .NET Core C# with an example:

1. **Routing**:
   Routing in ASP.NET Core maps incoming HTTP requests to the appropriate action methods in controllers based on the URL pattern. Routes are defined in the `Startup.cs` file using the `MapControllerRoute()` method.

   Example of configuring routing in `Startup.cs`:
   ```csharp
   public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
   {
       app.UseRouting();

       app.UseEndpoints(endpoints =>
       {
           endpoints.MapControllerRoute(
               name: "default",
               pattern: "{controller=Home}/{action=Index}/{id?}");
       });
   }
   ```
   This configuration sets up a default route that maps incoming requests to controller actions based on the URL pattern `{controller}/{action}/{id?}`.

2. **MVC Architecture**:
   The Model-View-Controller (MVC) pattern divides an application into three interconnected components: models, views, and controllers. Models represent the data and business logic, views display the user interface, and controllers handle user input and orchestrate interactions between models and views.

   Example of creating a controller in C#:
   ```csharp
   using Microsoft.AspNetCore.Mvc;

   public class HomeController : Controller
   {
       public IActionResult Index()
       {
           return View();
       }
   }
   ```
   In this example, the `HomeController` class inherits from `Controller` and defines an action method `Index()` that returns a view.

3. **Creating Views**:
   Views in ASP.NET Core are typically written using Razor syntax, a combination of HTML and C# code that allows for dynamic content generation.

   Example of creating a view (`Index.cshtml`):
   ```html
   <h1>Welcome to My ASP.NET Core Application!</h1>
   ```
   This view displays a simple welcome message using HTML.

4. **Accessing Models**:
   Models encapsulate the application's data and business logic. Controllers interact with models to retrieve data and pass it to views for rendering.

   Example of creating a model class in C#:
   ```csharp
   public class Product
   {
       public int Id { get; set; }
       public string Name { get; set; }
       public decimal Price { get; set; }
   }
   ```
   This `Product` class represents a product with properties for its ID, name, and price.

By following the MVC pattern and configuring routing, you can build structured and maintainable web applications in .NET Core C#. Controllers handle incoming requests, models represent the data, and views display the user interface, providing a clean separation of concerns and promoting code reusability and maintainability.