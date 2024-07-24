Creating a basic ASP.NET Core application can be done using the CLI (Command-Line Interface) or an Integrated Development Environment (IDE) like Visual Studio or Visual Studio Code. I'll provide instructions for both approaches.

### Using the CLI:

1. Open a command prompt or terminal.

2. Navigate to the directory where you want to create your ASP.NET Core application.

3. Run the following command to create a new ASP.NET Core web application:

   ```bash
   dotnet new web -n MyFirstAspNetCoreApp
   ```

   This command will create a new ASP.NET Core web application in a folder named "MyFirstAspNetCoreApp."

4. Change to the project directory:

   ```bash
   cd MyFirstAspNetCoreApp
   ```

5. To run the application, use the following command:

   ```bash
   dotnet run
   ```

   This will start a local development web server, and you'll see output indicating that the application is running.

6. Open your web browser and navigate to `http://localhost:5000` to view your basic ASP.NET Core application. You should see a "Hello World" message.

### Using Visual Studio Code (VS Code):

1. Open Visual Studio Code.

2. Install the "C# for Visual Studio Code" extension if you haven't already. You can do this by going to the Extensions view (Ctrl+Shift+X) and searching for "C#."

3. Create a new folder for your project and open it in VS Code.

4. In VS Code, open a terminal by clicking "Terminal" in the menu and selecting "New Terminal."

5. Run the following command to create a new ASP.NET Core web application:

   ```bash
   dotnet new web -n MyFirstAspNetCoreApp
   ```

6. Change to the project directory:

   ```bash
   cd MyFirstAspNetCoreApp
   ```

7. To run the application, use the following command:

   ```bash
   dotnet run
   ```

   This will start the local development web server.

8. Open your web browser and navigate to `http://localhost:5000` to view your basic ASP.NET Core application in VS Code. You should see the "Hello World" message.

### Using Visual Studio (Optional):

If you're using Visual Studio, you can create an ASP.NET Core application by selecting the appropriate project template in Visual Studio. Here's a high-level overview:

1. Open Visual Studio.

2. Click "File" > "New" > "Project."

3. In the "Create a new project" window, search for "ASP.NET Core Web Application."

4. Choose a project template, configure your project settings, and click "Create."

5. You can now use Visual Studio for coding, debugging, and running your ASP.NET Core application.

Whether you use the CLI or an IDE, you've now created a basic ASP.NET Core application. You can start building and customizing your web application from this point.