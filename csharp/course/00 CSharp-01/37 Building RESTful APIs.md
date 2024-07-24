Building RESTful APIs with .NET Core C# is a common use case, and it can be done effectively using ASP.NET Core. Here's a step-by-step guide to building RESTful APIs in .NET Core C#:

### 1. Create a New .NET Core Web API Project

Use the .NET Core CLI or Visual Studio to create a new .NET Core Web API project.

```bash
dotnet new webapi -n MyApi
```

### 2. Define Models

Define the data models that represent the resources in your API.

```csharp
public class TodoItem
{
    public int Id { get; set; }
    public string Name { get; set; }
    public bool IsComplete { get; set; }
}
```

### 3. Implement Controllers

Create controllers to handle HTTP requests and define API endpoints.

```csharp
[ApiController]
[Route("api/[controller]")]
public class TodoController : ControllerBase
{
    private readonly List<TodoItem> _todoItems = new List<TodoItem>();

    [HttpGet]
    public IEnumerable<TodoItem> GetAll()
    {
        return _todoItems;
    }

    [HttpGet("{id}", Name = "GetTodo")]
    public ActionResult<TodoItem> GetById(int id)
    {
        var todoItem = _todoItems.FirstOrDefault(x => x.Id == id);
        if (todoItem == null)
        {
            return NotFound();
        }
        return todoItem;
    }

    [HttpPost]
    public ActionResult<TodoItem> Create(TodoItem item)
    {
        item.Id = _todoItems.Count + 1;
        _todoItems.Add(item);

        return CreatedAtRoute("GetTodo", new { id = item.Id }, item);
    }

    [HttpPut("{id}")]
    public IActionResult Update(int id, TodoItem item)
    {
        var todoItem = _todoItems.FirstOrDefault(x => x.Id == id);
        if (todoItem == null)
        {
            return NotFound();
        }
        todoItem.Name = item.Name;
        todoItem.IsComplete = item.IsComplete;

        return NoContent();
    }

    [HttpDelete("{id}")]
    public IActionResult Delete(int id)
    {
        var todoItem = _todoItems.FirstOrDefault(x => x.Id == id);
        if (todoItem == null)
        {
            return NotFound();
        }
        _todoItems.Remove(todoItem);

        return NoContent();
    }
}
```

### 4. Configure Routing and Middleware

Configure routing and middleware in the `Startup.cs` file.

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddControllers();
}

public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseRouting();

    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapControllers();
    });
}
```

### 5. Test the API

Test the API endpoints using tools like Postman or Swagger UI.

### 6. Implement Additional Features

Add features like input validation, authentication, logging, and error handling based on your requirements.

### 7. Deploy the API

Deploy the API to your desired hosting environment, such as Azure App Service or Docker containers.

By following these steps, you can build RESTful APIs in .NET Core C# using ASP.NET Core. ASP.NET Core provides a robust framework for building scalable and high-performance APIs. Let me know if you need further clarification or more examples!