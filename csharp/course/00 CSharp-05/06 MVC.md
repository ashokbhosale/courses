**Understanding MVC Architecture and its Components:**

MVC (Model-View-Controller) architecture is a design pattern that divides an application into three interconnected components:

1. **Model:** The model represents the data and business logic of the application. It encapsulates the application's state and behavior, including data access, validation, and manipulation.

2. **View:** The view is responsible for presenting the user interface and rendering data to the user. It receives input from users and displays information based on the application's state.

3. **Controller:** The controller acts as an intermediary between the model and the view. It handles user input, processes requests, and updates the model or selects the appropriate view to render based on the user's actions.

**Separation of Concerns:**

The key principle of MVC architecture is the separation of concerns, which divides the application into distinct responsibilities:

- **Models:** Responsible for managing data and business logic.
  
- **Views:** Responsible for presenting the user interface and displaying data.
  
- **Controllers:** Responsible for handling user input, processing requests, and coordinating interactions between models and views.

This separation enables developers to focus on specific aspects of the application's functionality, promotes modularity and code reuse, and facilitates easier maintenance and testing.

**Implementing MVC Architecture in C# using ASP.NET Core MVC:**

Below is an example of implementing MVC architecture in C# using ASP.NET Core MVC:

```csharp
// Model
public class Task
{
    public int Id { get; set; }
    public string Title { get; set; }
    public string Description { get; set; }
}

// Controller
public class TaskController : Controller
{
    [HttpGet]
    public IActionResult Index()
    {
        var tasks = GetTasksFromDatabase(); // Assume this method retrieves tasks from the database
        return View(tasks);
    }

    private List<Task> GetTasksFromDatabase()
    {
        // Logic to retrieve tasks from the database
    }
}

// View (Index.cshtml)
@model List<Task>

@foreach (var task in Model)
{
    <div>
        <h3>@task.Title</h3>
        <p>@task.Description</p>
    </div>
}
```

In this example:
- The model represents a Task entity with properties such as Id, Title, and Description.
- The controller, TaskController, handles requests and interacts with the model to retrieve tasks from the database.
- The view, Index.cshtml, renders the user interface and displays tasks using Razor syntax. The view receives the list of tasks from the controller and iterates over them to generate HTML output.