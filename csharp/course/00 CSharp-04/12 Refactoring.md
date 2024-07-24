Refactoring is the process of restructuring existing code without changing its external behavior to improve its internal structure, readability, maintainability, and adherence to design principles. When refactoring code to adhere to design principles, it's essential to identify and address both design smells (issues with the overall architecture and design) and code smells (issues with specific pieces of code).

**Techniques for Refactoring to Adhere to Design Principles:**

1. **Extract Method:** Identify repeated code blocks and extract them into separate methods. This promotes the Single Responsibility Principle (SRP) by ensuring that each method has a single responsibility.
   
   ```csharp
   // Before refactoring
   public void CalculateTotalPrice()
   {
       // Calculate total price
       // Code block 1
       // Code block 2
       // Code block 3
   }
   
   // After refactoring
   public void CalculateTotalPrice()
   {
       CalculateSubTotal();
       ApplyDiscounts();
       CalculateTax();
   }

   private void CalculateSubTotal()
   {
       // Code block 1
       // Code block 2
   }

   private void ApplyDiscounts()
   {
       // Code block 3
   }

   private void CalculateTax()
   {
       // Code block 4
   }
   ```

2. **Extract Class:** If a class is doing too much, extract some of its responsibilities into separate classes. This helps adhere to the Single Responsibility Principle (SRP) and reduces complexity.

   ```csharp
   // Before refactoring
   public class Order
   {
       public void ProcessOrder()
       {
           // Processing logic
       }

       public void GenerateInvoice()
       {
           // Invoice generation logic
       }
   }
   
   // After refactoring
   public class Order
   {
       private OrderProcessor _orderProcessor;
       private InvoiceGenerator _invoiceGenerator;

       public Order()
       {
           _orderProcessor = new OrderProcessor();
           _invoiceGenerator = new InvoiceGenerator();
       }

       public void ProcessOrder()
       {
           _orderProcessor.ProcessOrder();
       }

       public void GenerateInvoice()
       {
           _invoiceGenerator.GenerateInvoice();
       }
   }
   ```

3. **Replace Conditional with Polymorphism:** If you have complex conditional logic, consider using polymorphism to simplify it. This promotes the Open/Closed Principle (OCP) and Liskov Substitution Principle (LSP).

   ```csharp
   // Before refactoring
   public class Shape
   {
       public void Draw()
       {
           if (Type == "Circle")
           {
               DrawCircle();
           }
           else if (Type == "Square")
           {
               DrawSquare();
           }
           // More conditional checks for other shapes
       }
   }
   
   // After refactoring
   public abstract class Shape
   {
       public abstract void Draw();
   }

   public class Circle : Shape
   {
       public override void Draw()
       {
           // Draw circle
       }
   }

   public class Square : Shape
   {
       public override void Draw()
       {
           // Draw square
       }
   }
   ```

**Identifying and Addressing Design Smells and Code Smells:**

1. **Design Smells:** Look for signs of poor design such as tight coupling, god classes, and violation of SOLID principles. Refactor the code to address these issues by applying appropriate design patterns and principles.

2. **Code Smells:** Use code analysis tools and manual code reviews to identify code smells such as duplicated code, long methods, and excessive nesting. Refactor the code to improve readability, maintainability, and adherence to best practices.

3. **Refactoring Tools:** Take advantage of refactoring tools available in IDEs such as Visual Studio and ReSharper to automate repetitive refactoring tasks and ensure consistency in code quality.

By consistently applying refactoring techniques and addressing design and code smells, you can improve the overall quality of your codebase, making it easier to maintain, extend, and understand.