Implementing API documentation using Swagger or OpenAPI in .NET Core provides a standardized way to describe, document, and visualize your API endpoints. This helps developers understand how to use your API effectively. Let's see how to implement API documentation using Swagger in a .NET Core application with an example.

### Example: Implementing API Documentation with Swagger in .NET Core

1. Install the Swashbuckle.AspNetCore NuGet package:

```bash
dotnet add package Swashbuckle.AspNetCore
```

2. Configure Swagger in `Startup.cs`:

```csharp
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Hosting;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;
using Microsoft.OpenApi.Models;
using System;

namespace YourNamespace
{
    public class Startup
    {
        public void ConfigureServices(IServiceCollection services)
        {
            services.AddControllers();

            services.AddSwaggerGen(c =>
            {
                c.SwaggerDoc("v1", new OpenApiInfo { Title = "Your API", Version = "v1" });
            });
        }

        public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
        {
            if (env.IsDevelopment())
            {
                app.UseDeveloperExceptionPage();
            }

            app.UseSwagger();
            app.UseSwaggerUI(c =>
            {
                c.SwaggerEndpoint("/swagger/v1/swagger.json", "Your API v1");
                c.RoutePrefix = string.Empty; // Serve the Swagger UI at the app's root URL
            });

            app.UseRouting();

            app.UseEndpoints(endpoints =>
            {
                endpoints.MapControllers();
            });
        }
    }
}
```

3. Add XML comments to your API controllers and models:

```csharp
using Microsoft.AspNetCore.Mvc;
using System.Collections.Generic;

namespace YourNamespace.Controllers
{
    [ApiController]
    [Route("api/[controller]")]
    public class ProductsController : ControllerBase
    {
        /// <summary>
        /// Gets all products.
        /// </summary>
        /// <returns>All products</returns>
        [HttpGet]
        public IEnumerable<Product> Get()
        {
            // Implementation
        }

        // Other actions

        /// <summary>
        /// Represents a product.
        /// </summary>
        public class Product
        {
            /// <summary>
            /// The ID of the product.
            /// </summary>
            public int Id { get; set; }

            /// <summary>
            /// The name of the product.
            /// </summary>
            public string Name { get; set; }

            // Other properties
        }
    }
}
```

4. Build and run your application. You can access the Swagger UI at `https://localhost:<port>/swagger`.

Now, your .NET Core API is documented using Swagger/OpenAPI. Developers can explore your API endpoints, test them, and understand their usage directly from the Swagger UI.