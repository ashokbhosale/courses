Creating desktop applications in .NET Core C# involves using frameworks like Windows Presentation Foundation (WPF) or Windows Forms. Here's a basic guide to getting started with each:

### Using Windows Presentation Foundation (WPF):

1. **Install Visual Studio**:
   - Ensure you have Visual Studio installed on your development machine. You can download it from the official Microsoft website.

2. **Create a New WPF Project**:
   - Open Visual Studio.
   - Go to `File > New > Project`.
   - Select "WPF App (.NET Core)" template.
   - Choose a name and location for your project.
   - Click "Create".

3. **Design Your User Interface (UI)**:
   - Use XAML (Extensible Application Markup Language) to design the UI of your application.
   - Open the `MainWindow.xaml` file to design your main window.
   - Use XAML elements like `<Grid>`, `<StackPanel>`, `<Button>`, etc., to create your UI.

4. **Write Code-Behind**:
   - Open the corresponding code-behind file (`MainWindow.xaml.cs`) to write C# code.
   - Implement event handlers and logic for UI elements.

5. **Run Your Application**:
   - Press `F5` or go to `Debug > Start Debugging` to run your application.

### Using Windows Forms:

1. **Install Visual Studio**:
   - Ensure you have Visual Studio installed on your development machine.

2. **Create a New Windows Forms Project**:
   - Open Visual Studio.
   - Go to `File > New > Project`.
   - Select "Windows Forms App (.NET Core)" template.
   - Choose a name and location for your project.
   - Click "Create".

3. **Design Your User Interface (UI)**:
   - Use the Visual Designer to design the UI of your application.
   - Drag and drop controls from the Toolbox onto the form.
   - Set properties and customize the layout as needed.

4. **Write Code**:
   - Double-click on UI elements to create event handlers.
   - Write C# code in the code-behind file (`Form1.cs`) to implement logic and handle events.

5. **Run Your Application**:
   - Press `F5` or go to `Debug > Start Debugging` to run your application.

Choose the framework that best fits your project requirements and familiarity. WPF offers more modern and flexible UI capabilities, while Windows Forms provides a simpler and more traditional approach to desktop application development.