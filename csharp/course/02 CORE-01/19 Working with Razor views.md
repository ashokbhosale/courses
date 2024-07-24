Working with Razor views in ASP.NET Core involves creating dynamic HTML content using Razor syntax, a combination of HTML and C# code. Here's an example of how to work with Razor views in .NET Core C#:

1. **Creating a Razor View**:
   - Create a new Razor view file with the `.cshtml` extension in the `Views` folder of your ASP.NET Core project.
   - Example of a simple Razor view (`Index.cshtml`):
     ```html
     <!DOCTYPE html>
     <html>
     <head>
         <title>My ASP.NET Core Application</title>
     </head>
     <body>
         <h1>Welcome to My ASP.NET Core Application!</h1>
         <p>The current time is: @DateTime.Now</p>
     </body>
     </html>
     ```
   - In this example, `@DateTime.Now` is a Razor code block that retrieves the current date and time and renders it in the HTML content.

2. **Passing Data to Razor Views**:
   - Data can be passed from controller actions to Razor views using the `View()` method or by specifying a model.
   - Example of passing data to a Razor view from a controller action:
     ```csharp
     using Microsoft.AspNetCore.Mvc;

     public class HomeController : Controller
     {
         public IActionResult Index()
         {
             ViewData["Message"] = "Welcome to my ASP.NET Core Application!";
             return View();
         }
     }
     ```
   - In the Razor view (`Index.cshtml`), the `ViewData` dictionary can be accessed to display the message:
     ```html
     <h1>@ViewData["Message"]</h1>
     ```

3. **Using Razor Layouts**:
   - Razor layouts allow you to define a common layout for multiple views and include shared content such as headers, footers, and navigation menus.
   - Example of creating a Razor layout (`_Layout.cshtml`):
     ```html
     <!DOCTYPE html>
     <html>
     <head>
         <title>@ViewData["Title"] - My ASP.NET Core Application</title>
     </head>
     <body>
         <header>
             <h1>My ASP.NET Core Application</h1>
         </header>
         <main>
             @RenderBody()
         </main>
         <footer>
             <p>&copy; 2022 My ASP.NET Core Application</p>
         </footer>
     </body>
     </html>
     ```
   - Views can use this layout by specifying it at the top of the Razor file:
     ```html
     @{
         Layout = "_Layout";
     }

     <!-- Rest of the view content here -->
     ```

By following these examples, you can create dynamic and responsive web pages using Razor views in ASP.NET Core with C#. Razor syntax enables you to seamlessly integrate C# code with HTML content, making it easy to generate dynamic content based on application logic.