Cross-Origin Resource Sharing (CORS) is a security feature implemented by web browsers to control which web domains can make requests to a given web domain. It is a mechanism that allows or restricts cross-origin requests in web applications.

When a web page hosted on one domain makes a request to a different domain (cross-origin request) using technologies like XMLHttpRequest or Fetch API, browsers enforce the Same-Origin Policy. CORS provides a way to relax this policy selectively.

**How CORS Works:**

1. **Preflight Request:**
   - For certain types of requests (e.g., those with custom headers or non-simple methods), the browser sends a preflight request using the HTTP OPTIONS method to check whether the actual request is safe to send.

2. **Access-Control-Allow-Origin Header:**
   - The server responds with the `Access-Control-Allow-Origin` header, specifying which origins are permitted to access the resource. This header can be a specific origin or a comma-separated list of origins.

3. **Simple Requests:**
   - For simple requests (GET, POST with specific content types), the browser automatically handles the request if the server includes the appropriate `Access-Control-Allow-Origin` header.

**Configuring CORS:**

To configure your API to allow or restrict cross-origin requests, you can set the `Access-Control-Allow-Origin` header in your server's HTTP responses.

1. **Allow All Origins:**
   - Allow any domain to access your API (not recommended for production unless necessary):
     ```
     Access-Control-Allow-Origin: *
     ```

2. **Allow Specific Origins:**
   - Allow only specific domains to access your API:
     ```
     Access-Control-Allow-Origin: https://allowed-domain.com
     ```

3. **Allow Multiple Origins:**
   - Allow multiple domains by specifying them in a comma-separated list:
     ```
     Access-Control-Allow-Origin: https://domain1.com, https://domain2.com
     ```

4. **Allow Credentials:**
   - If your API supports credentials (e.g., cookies), set the `Access-Control-Allow-Credentials` header to `true`:
     ```
     Access-Control-Allow-Credentials: true
     ```

5. **Allow Specific Headers and Methods:**
   - Specify which HTTP methods and headers are allowed:
     ```
     Access-Control-Allow-Methods: GET, POST, OPTIONS
     Access-Control-Allow-Headers: Content-Type, Authorization
     ```

**Example:**
```http
HTTP/1.1 200 OK
Access-Control-Allow-Origin: https://allowed-domain.com
Access-Control-Allow-Methods: GET, POST, OPTIONS
Access-Control-Allow-Headers: Content-Type, Authorization
Access-Control-Allow-Credentials: true
```

By configuring CORS properly, you can ensure that your API is accessible to authorized clients while maintaining security by controlling access from different origins.