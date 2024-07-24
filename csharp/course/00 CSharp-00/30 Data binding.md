Data binding in .NET Core C# allows you to establish a connection between the data source and the user interface elements, ensuring that changes in one are automatically reflected in the other. It simplifies the process of displaying and manipulating data in UI controls such as textboxes, list boxes, and grids. Here's an overview of data binding in .NET Core C#:

1. **Types of Data Binding**:
   - **One-Way Data Binding**: Data flows from the source (e.g., object property) to the target (e.g., UI control) but not the other way around.
   - **Two-Way Data Binding**: Data flows in both directions between the source and the target, allowing changes made in the UI to update the source and vice versa.
   - **One-Time Data Binding**: Data is only retrieved from the source once and not updated thereafter.

2. **Data Sources**:
   - Data binding can be established with various types of data sources, including objects, collections, databases, and services.
   - Common data sources include plain old CLR objects (POCOs), Entity Framework entities, LINQ queries, and JSON/XML data.

3. **Binding Expressions**:
   - Binding expressions are used to specify the relationship between the data source and the UI element.
   - They are typically written using markup languages like XAML or programmatically in code-behind files.

4. **Binding Modes**:
   - **OneWay**: Updates the target property when the source property changes.
   - **TwoWay**: Updates the target property when the source property changes, and vice versa.
   - **OneTime**: Updates the target property with the source value only once.

5. **Data Context**:
   - The data context serves as the source of data for a binding operation.
   - It provides the object or collection that the UI elements bind to.
   - In XAML, the data context can be set at various levels, such as the entire window, a specific control, or even individual elements.

6. **INotifyPropertyChanged Interface**:
   - For two-way data binding to work effectively, the source object should implement the `INotifyPropertyChanged` interface.
   - This interface defines an event (`PropertyChanged`) that notifies subscribers when a property value changes.

7. **Examples**:
   - **XAML Data Binding**:
     ```xml
     <TextBox Text="{Binding UserName, Mode=TwoWay}" />
     ```
   - **Code-Behind Data Binding**:
     ```csharp
     Binding binding = new Binding("UserName") { Source = viewModel, Mode = BindingMode.TwoWay };
     textBox.SetBinding(TextBox.TextProperty, binding);
     ```

Data binding simplifies the development of UI-intensive applications by reducing the amount of boilerplate code needed to keep UI elements synchronized with underlying data sources. It promotes separation of concerns, enhances code maintainability, and improves the overall user experience.