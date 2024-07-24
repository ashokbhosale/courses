Middleware is a powerful concept in web development that allows you to process requests and responses in a modular and reusable way. I'll show you how to implement middleware in two popular API frameworks: Express.js (Node.js) and ASP.NET Core (C#).

**1. Express.js Middleware:**

Express.js is a popular web application framework for Node.js. Middleware functions in Express.js have access to the request object (`req`), the response object (`res`), and the next middleware function in the application’s request-response cycle.

Here's an example of a simple middleware that logs information about each incoming request:

```javascript
const express = require('express');
const app = express();

// Custom middleware function
const loggerMiddleware = (req, res, next) => {
  console.log(`Request received: ${req.method} ${req.url}`);
  next(); // Pass control to the next middleware in the stack
};

// Use the middleware for all routes
app.use(loggerMiddleware);

// Your API routes and logic go here

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
  console.log(`Server is running on port ${PORT}`);
});
```

In this example, the `loggerMiddleware` function logs information about each incoming request before passing control to the next middleware in the stack.

**2. ASP.NET Core Middleware:**

ASP.NET Core is a cross-platform, high-performance framework for building modern, cloud-based, and internet-connected applications. Middleware in ASP.NET Core is arranged in a pipeline, and each middleware component in the pipeline processes an HTTP request or response.

Here's an example of middleware in ASP.NET Core that adds a custom header to every response:

```csharp
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Http;
using Microsoft.Extensions.DependencyInjection;

public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Configure services if needed
    }

    public void Configure(IApplicationBuilder app)
    {
        // Custom middleware to add a custom header to every response
        app.Use(async (context, next) =>
        {
            context.Response.Headers.Add("X-Custom-Header", "Hello from custom middleware");
            await next(); // Pass control to the next middleware in the pipeline
        });

        // Configure routing, MVC, or other middleware components here

        app.Run(async (context) =>
        {
            await context.Response.WriteAsync("Hello, ASP.NET Core!");
        });
    }
}
```

In this example, the custom middleware adds a custom header (`X-Custom-Header`) to every HTTP response.

Middleware in ASP.NET Core can be more complex, with features like dependency injection and the ability to handle different stages of the request-response pipeline.

Both Express.js and ASP.NET Core provide a flexible and powerful middleware system, allowing you to customize request and response processing in your API.