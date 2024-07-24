Developing RESTful Web APIs using ASP.NET Core is a common task for building web services that expose data and functionality over HTTP. ASP.NET Core provides powerful features for building RESTful APIs, including attribute routing, request/response formatting, and versioning. Here's a guide on how to create RESTful Web APIs with these features:

### Create an ASP.NET Core Web API Project:

1. **Create a New ASP.NET Core Project**:
   - Using the .NET CLI or Visual Studio, create a new ASP.NET Core Web API project.

   ```bash
   dotnet new webapi -n YourApiName
   ```

2. **Configure Startup.cs**:
   - In the `Startup.cs` file, configure the services and middleware for your API.

   ```csharp
   public void ConfigureServices(IServiceCollection services)
   {
       // Configure services, e.g., add database context, authentication, etc.
   }

   public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
   {
       // Configure middleware, e.g., routing, error handling, authentication, etc.
   }
   ```

### Attribute Routing:

ASP.NET Core supports attribute routing, which allows you to define routes directly on your controller actions. This provides a clean and flexible way to define API routes.

1. **Enable Attribute Routing**:
   - In the `Startup.cs` file, add the following code to enable attribute routing:

   ```csharp
   services.AddControllers();
   ```

2. **Define Routes**:
   - Use the `[Route]` attribute on controller actions to define the route template.

   ```csharp
   [Route("api/[controller]")]
   [ApiController]
   public class ProductsController : ControllerBase
   {
       [HttpGet]
       public ActionResult<IEnumerable<Product>> GetProducts()
       {
           // Your action logic
       }

       [HttpGet("{id}")]
       public ActionResult<Product> GetProduct(int id)
       {
           // Your action logic
       }
   }
   ```

### Request/Response Formatting:

1. **Input Model**:
   - Create input models (DTOs) for request data.

   ```csharp
   public class CreateProductDto
   {
       public string Name { get; set; }
       public decimal Price { get; set; }
   }
   ```

2. **Request Data Binding**:
   - Use model binding to automatically map incoming JSON or form data to action method parameters.

   ```csharp
   [HttpPost]
   public IActionResult CreateProduct([FromBody] CreateProductDto productDto)
   {
       // Your action logic
   }
   ```

3. **Response Data Formatting**:
   - Use the `ActionResult<T>` class to return data with appropriate HTTP status codes.

   ```csharp
   [HttpGet]
   public ActionResult<IEnumerable<Product>> GetProducts()
   {
       var products = _repository.GetProducts();
       return Ok(products);
   }
   ```

### API Versioning:

Versioning is important for maintaining backward compatibility and evolving your API over time. You can use the Microsoft.AspNetCore.Mvc.Versioning package to handle API versioning.

1. **Install the Versioning Package**:
   - Install the `Microsoft.AspNetCore.Mvc.Versioning` package in your project.

   ```bash
   dotnet add package Microsoft.AspNetCore.Mvc.Versioning
   ```

2. **Configure API Versioning**:
   - In the `Startup.cs` file, configure API versioning by adding services and middleware.

   ```csharp
   services.AddApiVersioning(options =>
   {
       options.DefaultApiVersion = new ApiVersion(1, 0);
       options.AssumeDefaultVersionWhenUnspecified = true;
       options.ReportApiVersions = true;
   });
   ```

3. **Version Attribute**:
   - Use the `[ApiVersion]` attribute to specify the version for your controller or action.

   ```csharp
   [ApiVersion("1.0")]
   [Route("api/v{version:apiVersion}/[controller]")]
   [ApiController]
   public class ProductsController : ControllerBase
   {
       // Your actions
   }
   ```

With these steps, you can create RESTful Web APIs in ASP.NET Core that include attribute routing for clean and flexible route definition, request/response formatting for data exchange, and API versioning to handle API evolution and backward compatibility.