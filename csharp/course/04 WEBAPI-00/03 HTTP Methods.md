Certainly! Let's add PATCH to the mix:

1. **GET:**
   - **Purpose:** Used for retrieving data from a specified resource.
   - **Characteristics:** It should only retrieve data and not modify anything on the server. Requests are typically idempotent.

   Example:
   ```http
   GET /users/123
   ```

2. **POST:**
   - **Purpose:** Used for submitting data to be processed to a specified resource.
   - **Characteristics:** It often results in the creation of a new resource on the server. It's not idempotent.

   Example:
   ```http
   POST /users
   Content-Type: application/json

   {
     "name": "John Doe",
     "email": "john@example.com"
   }
   ```

3. **PUT:**
   - **Purpose:** Used for updating a specified resource or creating a new resource if it doesn't exist.
   - **Characteristics:** It's idempotent.

   Example:
   ```http
   PUT /users/123
   Content-Type: application/json

   {
     "name": "Updated Name"
   }
   ```

4. **DELETE:**
   - **Purpose:** Used for deleting a specified resource.
   - **Characteristics:** It's idempotent.

   Example:
   ```http
   DELETE /users/123
   ```

5. **PATCH:**
   - **Purpose:** Used for applying partial modifications to a resource.
   - **Characteristics:** It's typically used when you want to apply only a subset of changes to a resource, rather than updating the entire resource. It's not always idempotent.

   Example:
   ```http
   PATCH /users/123
   Content-Type: application/json

   {
     "name": "Updated Name"
   }
   ```

Including PATCH in your API allows for more granular updates, which can be useful when you don't want to send the entire resource for modification.

These HTTP methods provide a versatile set of actions for interacting with resources in a RESTful API. Understanding their characteristics and use cases is crucial for designing effective and efficient APIs.