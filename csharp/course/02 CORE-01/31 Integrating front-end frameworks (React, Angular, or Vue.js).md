Integrating front-end frameworks like React, Angular, or Vue.js with .NET Core C# involves building a backend API using .NET Core and connecting it with the front-end application built using the chosen framework. Let's take React.js as an example:

1. **Create a .NET Core Web API Project**:
   - Begin by creating a new ASP.NET Core Web API project using the `dotnet` CLI or Visual Studio.
   ```bash
   dotnet new webapi -n MyWebApi
   ```

2. **Implement API Endpoints**:
   - Define your API endpoints and business logic to handle requests and responses.
   ```csharp
   [Route("api/[controller]")]
   [ApiController]
   public class ProductsController : ControllerBase
   {
       private readonly ProductService _productService;

       public ProductsController(ProductService productService)
       {
           _productService = productService;
       }

       [HttpGet]
       public ActionResult<IEnumerable<Product>> Get()
       {
           var products = _productService.GetAllProducts();
           return Ok(products);
       }

       [HttpGet("{id}")]
       public ActionResult<Product> Get(int id)
       {
           var product = _productService.GetProductById(id);
           if (product == null)
           {
               return NotFound();
           }
           return Ok(product);
       }

       // Other CRUD actions (POST, PUT, DELETE) omitted for brevity
   }
   ```

3. **Install Required Packages**:
   - Install necessary packages using npm or yarn for your front-end framework (React, Angular, or Vue.js).
   ```bash
   npm install axios     # For making HTTP requests
   ```

4. **Create Front-End Application**:
   - Create a new React application using create-react-app or any other method.
   ```bash
   npx create-react-app my-react-app
   ```

5. **Fetch Data from API**:
   - Use Axios or Fetch API to make HTTP requests to your .NET Core Web API endpoints from your React components.
   ```javascript
   import React, { useState, useEffect } from 'react';
   import axios from 'axios';

   function ProductList() {
       const [products, setProducts] = useState([]);

       useEffect(() => {
           axios.get('https://localhost:5001/api/products')
               .then(response => {
                   setProducts(response.data);
               })
               .catch(error => {
                   console.error('Error fetching data: ', error);
               });
       }, []);

       return (
           <div>
               <h2>Products</h2>
               <ul>
                   {products.map(product => (
                       <li key={product.id}>{product.name}</li>
                   ))}
               </ul>
           </div>
       );
   }

   export default ProductList;
   ```

6. **Run Both Applications**:
   - Run your .NET Core Web API project and your React application concurrently.
   ```bash
   dotnet run     # Run .NET Core Web API
   npm start      # Run React application
   ```

7. **Test Integration**:
   - Test the integration by accessing your React application in the browser and verifying that it successfully fetches and displays data from the .NET Core Web API.

By following these steps, you can integrate front-end frameworks like React, Angular, or Vue.js with .NET Core C# to build full-stack web applications. The same approach can be adapted for integrating Angular or Vue.js by creating their respective projects and making HTTP requests to the .NET Core Web API.