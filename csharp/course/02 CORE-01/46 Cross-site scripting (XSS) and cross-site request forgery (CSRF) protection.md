Protecting against Cross-Site Scripting (XSS) and Cross-Site Request Forgery (CSRF) attacks is critical for ensuring the security of your .NET Core C# web applications. Here's how you can implement protection against XSS and CSRF:

### Cross-Site Scripting (XSS) Protection:

#### 1. Input Validation and Output Encoding:

Ensure that all user input is properly validated and encoded before being displayed in the UI to prevent XSS attacks.

#### Example:

```csharp
public IActionResult DisplayMessage(string message)
{
    ViewData["Message"] = WebUtility.HtmlEncode(message); // Encode user input before displaying
    return View();
}
```

#### 2. Content Security Policy (CSP):

Implement a Content Security Policy to restrict the sources from which content can be loaded, thereby mitigating XSS attacks.

#### Example:

In `Startup.cs`, configure CSP middleware:

```csharp
public void Configure(IApplicationBuilder app)
{
    app.Use(async (context, next) =>
    {
        context.Response.Headers.Add("Content-Security-Policy", "default-src 'self'");
        await next();
    });
}
```

### Cross-Site Request Forgery (CSRF) Protection:

#### 1. Anti-Forgery Tokens:

Generate and validate anti-forgery tokens for each user request to prevent CSRF attacks.

#### Example:

In your form, include an anti-forgery token:

```html
@using Microsoft.AspNetCore.Antiforgery
@inject IAntiforgery Antiforgery

<form method="post">
    @Antiforgery.GetHtml()
    <!-- Other form fields -->
</form>
```

In your controller, validate the anti-forgery token:

```csharp
[HttpPost]
[ValidateAntiForgeryToken]
public IActionResult SubmitForm(MyViewModel model)
{
    if (!ModelState.IsValid)
    {
        // Handle invalid model state
    }

    // Proceed with form submission
}
```

### Conclusion:

Implementing protection against XSS and CSRF attacks is essential for securing your .NET Core C# web applications. By following best practices such as input validation, output encoding, Content Security Policy (CSP), and anti-forgery tokens, you can significantly reduce the risk of these common security vulnerabilities. Always stay updated on the latest security threats and mitigation techniques to ensure the ongoing security of your applications.