Building responsive web applications with .NET Core C# involves creating layouts and designs that adapt and adjust to different screen sizes and devices. Here's how you can achieve this with examples:

1. **Use CSS Frameworks**:
   - CSS frameworks like Bootstrap, Foundation, or Bulma provide pre-built components and responsive grid systems that you can use to quickly create responsive layouts.

   Example using Bootstrap:
   ```html
   <!-- Include Bootstrap CSS -->
   <link href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" rel="stylesheet">

   <!-- Example responsive layout -->
   <div class="container">
       <div class="row">
           <div class="col-sm">
               Column 1
           </div>
           <div class="col-sm">
               Column 2
           </div>
           <div class="col-sm">
               Column 3
           </div>
       </div>
   </div>
   ```

2. **Use CSS Media Queries**:
   - CSS Media Queries allow you to apply different styles based on the device's screen size and characteristics.

   Example CSS Media Queries:
   ```css
   /* Example media query for smaller screens */
   @media screen and (max-width: 768px) {
       /* CSS styles for smaller screens */
   }
   ```

3. **Viewport Meta Tag**:
   - Include the viewport meta tag in your HTML to ensure proper scaling and rendering on mobile devices.

   Example viewport meta tag:
   ```html
   <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
   ```

4. **Flexbox and Grid Layout**:
   - Utilize Flexbox and CSS Grid Layout for creating flexible and responsive layouts.

   Example using Flexbox:
   ```css
   .container {
       display: flex;
       flex-wrap: wrap;
   }

   .item {
       flex: 1 0 20%; /* 20% width for each item */
   }
   ```

5. **Responsive Images**:
   - Use the `max-width: 100%;` CSS property to ensure images scale appropriately on different screen sizes.

   Example responsive image:
   ```css
   img {
       max-width: 100%;
       height: auto;
   }
   ```

6. **Test Across Multiple Devices**:
   - Test your web application across various devices and screen sizes to ensure proper responsiveness.

7. **.NET Core Views**:
   - If you're using ASP.NET Core MVC, ensure that your views are designed to be responsive by applying appropriate CSS classes and styles.

   Example using ASP.NET Core Views:
   ```csharp
   <div class="container">
       <div class="row">
           <div class="col-sm">
               Column 1
           </div>
           <div class="col-sm">
               Column 2
           </div>
           <div class="col-sm">
               Column 3
           </div>
       </div>
   </div>
   ```

By following these techniques and examples, you can build responsive web applications with .NET Core C#. Ensuring responsiveness is crucial for providing a consistent and user-friendly experience across different devices and screen sizes.