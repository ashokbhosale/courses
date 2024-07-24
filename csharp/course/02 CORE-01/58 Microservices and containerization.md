Microservices architecture and containerization are powerful concepts that can be effectively implemented using .NET Core C#. Here's how you can build microservices and containerize them using .NET Core:

### 1. Microservices Architecture:

In a microservices architecture, an application is divided into smaller, independently deployable services, each responsible for a specific business domain.

#### Example:

Let's consider an e-commerce application. You can break it down into microservices such as User Service (handling user management), Product Service (managing products), Order Service (handling orders), and Payment Service (processing payments).

### 2. Building Microservices with .NET Core:

Use ASP.NET Core to build microservices. Each microservice can be a separate ASP.NET Core web application.

#### Example:

```csharp
// User Microservice
public class UserController : ControllerBase
{
    private readonly IUserService _userService;

    public UserController(IUserService userService)
    {
        _userService = userService;
    }

    [HttpGet("{id}")]
    public async Task<IActionResult> GetUser(int id)
    {
        var user = await _userService.GetUserAsync(id);
        if (user == null)
        {
            return NotFound();
        }
        return Ok(user);
    }
}

// Product Microservice
public class ProductController : ControllerBase
{
    private readonly IProductService _productService;

    public ProductController(IProductService productService)
    {
        _productService = productService;
    }

    [HttpGet("{id}")]
    public async Task<IActionResult> GetProduct(int id)
    {
        var product = await _productService.GetProductAsync(id);
        if (product == null)
        {
            return NotFound();
        }
        return Ok(product);
    }
}
```

### 3. Containerization with Docker:

Containerization allows you to package microservices and their dependencies into lightweight, portable containers.

#### Example:

Create a Dockerfile for each microservice to define the container environment and build process:

```Dockerfile
# Dockerfile for User Microservice
FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /app
COPY . .
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "UserMicroservice.dll"]
```

Build the Docker image and run the container:

```bash
docker build -t user-microservice .
docker run -d -p 5000:80 user-microservice
```

### Conclusion:

By building microservices with .NET Core and containerizing them with Docker, you can achieve a scalable, resilient, and easily deployable architecture. Each microservice can be developed, tested, and deployed independently, enabling rapid development and continuous delivery. Containerization provides consistency across different environments and simplifies the deployment process. Combine these techniques with orchestration tools like Kubernetes for efficient management of microservices in production environments.