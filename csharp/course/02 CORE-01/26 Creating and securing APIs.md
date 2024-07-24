Creating and securing APIs in .NET Core C# involves building endpoints to handle incoming requests and implementing security measures to protect the API from unauthorized access. Let's walk through the process of creating and securing APIs with an example:

1. **Creating a .NET Core Web API Project**:
   - Create a new ASP.NET Core Web API project using the `dotnet` CLI or Visual Studio.
   - Example using the `dotnet` CLI:
     ```bash
     dotnet new webapi -n MyWebApi
     ```
   - This command creates a new ASP.NET Core Web API project named "MyWebApi".

2. **Defining a Model**:
   - Define a model class to represent the data structure of the resource.
   - Example of a simple model class in C#:
     ```csharp
     public class Product
     {
         public int Id { get; set; }
         public string Name { get; set; }
         public decimal Price { get; set; }
     }
     ```
   - This `Product` class represents a product with properties for its ID, name, and price.

3. **Creating Controller Actions**:
   - Create controller actions to handle HTTP requests and perform CRUD operations on the resource.
   - Example of a controller in C#:
     ```csharp
     using Microsoft.AspNetCore.Mvc;
     using System.Collections.Generic;

     [Route("api/[controller]")]
     [ApiController]
     public class ProductsController : ControllerBase
     {
         private static List<Product> _products = new List<Product>();

         [HttpGet]
         public IActionResult Get()
         {
             return Ok(_products);
         }

         [HttpPost]
         public IActionResult Post(Product product)
         {
             _products.Add(product);
             return CreatedAtAction(nameof(Get), new { id = product.Id }, product);
         }

         // Other CRUD actions omitted for brevity
     }
     ```
   - This `ProductsController` class defines actions to get all products and add a new product.

4. **Securing the API**:
   - Implement authentication and authorization to secure the API endpoints.
   - Example of implementing JWT authentication in `Startup.cs`:
     ```csharp
     services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
             .AddJwtBearer(options =>
             {
                 options.TokenValidationParameters = new TokenValidationParameters
                 {
                     ValidateIssuer = true,
                     ValidateAudience = true,
                     ValidateLifetime = true,
                     ValidateIssuerSigningKey = true,
                     ValidIssuer = Configuration["Jwt:Issuer"],
                     ValidAudience = Configuration["Jwt:Audience"],
                     IssuerSigningKey = new SymmetricSecurityKey(Encoding.UTF8.GetBytes(Configuration["Jwt:Key"]))
                 };
             });
     ```
   - This code configures JWT authentication using the provided JWT token parameters.

5. **Applying Authorization Policies**:
   - Use authorization policies to control access to API endpoints based on user roles or claims.
   - Example of applying an authorization policy to a controller action:
     ```csharp
     [Authorize(Roles = "Admin")]
     [HttpPost]
     public IActionResult Post(Product product)
     {
         _products.Add(product);
         return CreatedAtAction(nameof(Get), new { id = product.Id }, product);
     }
     ```
   - This action is restricted to users with the "Admin" role.

By following these steps and examples, you can create and secure APIs in .NET Core C#. Implementing authentication and authorization helps protect your API endpoints and ensures that only authorized users can access sensitive resources.