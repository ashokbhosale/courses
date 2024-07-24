Integration testing in .NET Core C# involves testing the interactions between various components or modules of your application to ensure they work together correctly. Let's see how to perform integration testing with an example:

### Example Scenario
Suppose you have a simple web API for managing products, and you want to write integration tests to verify that the API endpoints work as expected.

1. **Create Integration Test Project**:
   - Create a new .NET Core project for integration tests in your solution.
   ```bash
   dotnet new xunit -n MyIntegrationTests
   ```

2. **Install Required Packages**:
   - Install necessary packages like `Microsoft.AspNetCore.Mvc.Testing` for testing ASP.NET Core applications.
   ```bash
   dotnet add package Microsoft.AspNetCore.Mvc.Testing
   ```

3. **Write Integration Tests**:
   - Write integration tests to verify the behavior of your API endpoints.
   ```csharp
   using System.Net;
   using System.Net.Http;
   using System.Threading.Tasks;
   using Microsoft.AspNetCore.Mvc.Testing;
   using Xunit;

   namespace MyIntegrationTests
   {
       public class ProductsIntegrationTests : IClassFixture<WebApplicationFactory<Startup>>
       {
           private readonly WebApplicationFactory<Startup> _factory;

           public ProductsIntegrationTests(WebApplicationFactory<Startup> factory)
           {
               _factory = factory;
           }

           [Fact]
           public async Task Get_Products_ReturnsSuccessStatusCode()
           {
               // Arrange
               var client = _factory.CreateClient();

               // Act
               var response = await client.GetAsync("/api/products");

               // Assert
               response.EnsureSuccessStatusCode();
               Assert.Equal(HttpStatusCode.OK, response.StatusCode);
           }

           // More integration tests for other endpoints
       }
   }
   ```

4. **Startup Class for Testing**:
   - Configure your application's startup class to use a test-specific configuration.
   ```csharp
   public class Startup
   {
       public void ConfigureServices(IServiceCollection services)
       {
           // Configure services for testing
       }

       public void Configure(IApplicationBuilder app)
       {
           // Configure middleware for testing
       }
   }
   ```

5. **Run Integration Tests**:
   - Run integration tests using the test runner in Visual Studio or run tests from the command line using `dotnet test`.

### Example Web API Controller

```csharp
[ApiController]
[Route("api/[controller]")]
public class ProductsController : ControllerBase
{
    private readonly IProductService _productService;

    public ProductsController(IProductService productService)
    {
        _productService = productService;
    }

    [HttpGet]
    public ActionResult<IEnumerable<Product>> Get()
    {
        var products = _productService.GetAllProducts();
        return Ok(products);
    }

    // Other CRUD actions (POST, PUT, DELETE) omitted for brevity
}
```

By following these steps and examples, you can perform integration testing in .NET Core C#. Integration tests help ensure that different parts of your application work together correctly, providing confidence in the overall behavior of your software.