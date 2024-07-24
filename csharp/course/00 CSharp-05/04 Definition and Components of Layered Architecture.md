**Definition and Components of Layered Architecture:**

Layered architecture, also known as n-tier architecture, is a software design pattern that organizes a system into a set of horizontal layers, with each layer responsible for a specific aspect of functionality. The layers are typically arranged hierarchically, with higher-level layers depending on lower-level layers. The common layers in a layered architecture include:

1. **Presentation Layer:** This layer is responsible for presenting the user interface and handling user interactions. It includes components such as UI elements, controllers, and views.

2. **Application Layer (Business Logic):** The application layer contains the business logic of the system, including data processing, validation, and workflow management. It encapsulates the core functionality of the application.

3. **Data Access Layer:** The data access layer interacts with the underlying data storage, such as databases or external services. It is responsible for reading and writing data and handling data access logic.

**Advantages of Layered Architecture:**

- **Modularity:** The separation of concerns into distinct layers promotes modularity and allows for easier management and maintenance of the codebase.
  
- **Scalability:** Layered architecture facilitates scalability by enabling individual layers to be scaled independently based on demand.
  
- **Reusability:** Components within each layer can be reused across different parts of the system or in other projects, leading to improved productivity and reduced development time.
  
- **Abstraction:** Each layer provides a level of abstraction, allowing developers to focus on specific aspects of the system without being concerned with the implementation details of other layers.

**Disadvantages of Layered Architecture:**

- **Performance Overhead:** The strict separation between layers can introduce overhead in terms of communication and data transfer between layers, potentially impacting performance.
  
- **Complexity:** Managing dependencies and interactions between layers can become complex, especially in large-scale systems with multiple layers and components.
  
- **Rigidity:** Changes to one layer may require corresponding changes in other layers, leading to tight coupling and reduced flexibility in the system.

**Implementing Layered Architecture in C# Applications:**

Below is an example of how to implement a simple layered architecture in a .NET Core C# application:

```csharp
// Presentation Layer (ASP.NET Core MVC)
public class TaskController : Controller
{
    private readonly ITaskService _taskService;

    public TaskController(ITaskService taskService)
    {
        _taskService = taskService;
    }

    public IActionResult Index()
    {
        var tasks = _taskService.GetAllTasks();
        return View(tasks);
    }

    // Other action methods
}

// Application Layer (Business Logic)
public interface ITaskService
{
    IEnumerable<Task> GetAllTasks();
}

public class TaskService : ITaskService
{
    private readonly ITaskRepository _taskRepository;

    public TaskService(ITaskRepository taskRepository)
    {
        _taskRepository = taskRepository;
    }

    public IEnumerable<Task> GetAllTasks()
    {
        return _taskRepository.GetAllTasks();
    }
}

// Data Access Layer
public interface ITaskRepository
{
    IEnumerable<Task> GetAllTasks();
}

public class TaskRepository : ITaskRepository
{
    private readonly ApplicationDbContext _dbContext;

    public TaskRepository(ApplicationDbContext dbContext)
    {
        _dbContext = dbContext;
    }

    public IEnumerable<Task> GetAllTasks()
    {
        return _dbContext.Tasks.ToList();
    }
}
```

In this example:
- The Presentation Layer is implemented using ASP.NET Core MVC, with the TaskController handling HTTP requests and responses.
- The Application Layer contains the business logic, defined by the ITaskService interface and implemented by the TaskService class.
- The Data Access Layer interfaces with the database using Entity Framework Core, with the ITaskRepository interface defining data access operations and the TaskRepository class providing the implementation.