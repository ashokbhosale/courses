**Introduction to Architectural Patterns:**

Architectural patterns are high-level structures that provide solutions to common architectural problems encountered in software development. These patterns define the overall layout and organization of a software system, guiding the design of its components, relationships, and interactions. Architectural patterns help developers create scalable, maintainable, and flexible systems by providing proven blueprints for organizing code and implementing key architectural concepts.

**Overview of Common Architectural Patterns:**

1. **Layered Architecture:** Layered architecture organizes a system into horizontal layers, each responsible for a specific aspect of functionality. Common layers include presentation, business logic, and data access. This pattern promotes modularity, separation of concerns, and ease of maintenance.

2. **Client-Server Architecture:** Client-server architecture divides the system into client and server components, where clients request services from servers. This pattern facilitates scalability, as multiple clients can interact with a single server, and promotes centralized management of data and resources.

3. **Microservices Architecture:** Microservices architecture decomposes a system into small, independent services, each responsible for a specific business capability. Each service runs in its own process and communicates with other services via lightweight protocols such as HTTP or messaging. This pattern enables flexibility, scalability, and continuous delivery.

4. **Model-View-Controller (MVC):** MVC architecture separates the system into three components: Model (data and business logic), View (presentation layer), and Controller (handles user input and orchestrates interactions between Model and View). This pattern promotes separation of concerns, enabling easier maintenance and testing.

5. **Event-Driven Architecture (EDA):** Event-driven architecture decouples components by allowing them to communicate asynchronously via events or messages. This pattern enables loose coupling, scalability, and flexibility in handling complex workflows and interactions.

**Comparison of Architectural Patterns:**

- **Layered vs. Microservices:** Layered architecture is suitable for monolithic applications with a single codebase, whereas microservices architecture is ideal for large-scale, distributed systems with independent deployment and scaling requirements.
  
- **Client-Server vs. Microservices:** Client-server architecture is suitable for centralized systems with a single server, while microservices architecture is better suited for distributed systems with multiple services running independently.
  
- **MVC vs. MVVM:** MVC architecture is well-suited for web applications with server-side rendering, while MVVM (Model-View-ViewModel) architecture is commonly used in client-side applications with rich user interfaces, such as desktop or mobile apps.
  
- **Layered vs. Event-Driven:** Layered architecture promotes modularization and separation of concerns, while event-driven architecture enables loose coupling and asynchronous communication between components.

**Example in .NET Core C#:**

Let's consider an example of a simple web application using the MVC architectural pattern in .NET Core C#:

```csharp
// Model
public class Task
{
    public int Id { get; set; }
    public string Title { get; set; }
    public string Description { get; set; }
    // Additional properties and methods
}

// Controller
public class TaskController : Controller
{
    private readonly ITaskRepository _taskRepository;

    public TaskController(ITaskRepository taskRepository)
    {
        _taskRepository = taskRepository;
    }

    public IActionResult Index()
    {
        var tasks = _taskRepository.GetAllTasks();
        return View(tasks);
    }

    // Implement other action methods
}

// View
@model IEnumerable<Task>

@foreach (var task in Model)
{
    <div>
        <h3>@task.Title</h3>
        <p>@task.Description</p>
    </div>
}
```

In this example, the MVC architectural pattern separates the application into three components: Model (Task), View (Razor view), and Controller (TaskController). This separation of concerns enables easier maintenance, testing, and scalability of the application.