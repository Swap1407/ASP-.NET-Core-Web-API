# **ASP.NET Core Web API**
## **Introduction to ASP.NET Core Web API**
<details>
<summary> ---Expand--- </summary>

## **Why Do We Need Web APIs?**

### **Problems Without Web APIs**

When developing applications like a website, Android app, or iOS app that directly connect to a shared database, the following challenges arise:

- **Duplicate Logic:** Business logic is duplicated across different platforms.
- **Error-Prone Code:** Maintaining consistency across multiple applications increases the likelihood of errors.
- **Limited Communication:** Some front-end frameworks (e.g., Angular) cannot directly interact with databases.
- **Complex Maintenance:** Managing similar code across platforms becomes difficult and inefficient.

### **Solution: Web APIs**

A **Web API** provides a centralized communication interface between the database and various client applications, as shown below:

```
[Website]      [Android App]      [iOS App]
      \             |              /
       \            |             /
        \_______[Web API]________/
                    |
             [Database]
```

### **Advantages of Web APIs**

- **Platform Independence:** APIs work across different clients (web, mobile, IoT) via HTTP.
- **Lightweight Communication:** Supports formats like JSON and XML for efficient data exchange.
- **Centralized Logic:** Reduces code duplication and ensures consistency.
- **Security:** Provides mechanisms for authentication and authorization.
- **Scalability:** Allows for easy integration with new platforms or features.

---

## **What is Web API?**

A **Web API** is a set of rules that allows applications to communicate with each other over the internet. It is built on HTTP and commonly uses RESTful principles to exchange data.

Example Web API Endpoints:
- `GET /weather/today?location=London` - Retrieves today’s weather for London.
- `POST /books` - Adds a new book to the system.

---

## **What is ASP.NET Core Web API?**

**ASP.NET Core Web API** is a lightweight framework provided by Microsoft for building RESTful HTTP services. It is part of the ASP.NET Core framework and is ideal for creating APIs that can be consumed by a wide range of clients, including web browsers, mobile apps, and IoT devices.

### **Key Features of ASP.NET Core Web API**

- Cross-platform support (Windows, macOS, Linux).
- Built-in dependency injection.
- Lightweight and fast, using the ASP.NET Core runtime.
- Secure, with features like authentication and authorization.
- Easily integrates with modern front-end frameworks (React, Angular, etc.).

---

## **Why Do We Need ASP.NET Core Web API?**

ASP.NET Core Web API is essential for modern application development because it:

- Facilitates **cross-platform development** by enabling all client types to interact with the same API.
- Supports **stateless communication**, which is essential for REST principles.
- Provides a robust **pipeline for handling HTTP requests**.
- Ensures **high performance** with minimal resource usage.

---

## **What is REST?**

**REST** (Representational State Transfer) is an architectural style used for building scalable web services. RESTful APIs use HTTP methods and resources to perform CRUD operations.

### **Key REST Principles**

1. **Statelessness:** Each API call is independent and does not rely on previous interactions.
2. **Resource-Based URLs:** Resources are identified by URLs (e.g., `/products/1` for Product ID 1).
3. **HTTP Methods:** Standard methods like GET, POST, PUT, DELETE are used for communication.
4. **Representation:** Resources are typically represented using JSON or XML.
5. **Cacheability:** Responses should indicate whether they can be cached to improve performance.

---

## **Difference between ASP.NET Web API and ASP.NET Core Web API**

| **Aspect**              | **ASP.NET Web API**                                                                 | **ASP.NET Core Web API**                                                                                                     |
|--------------------------|-------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|
| **Platform Support**     | Built on the .NET Framework, runs only on Windows.                                   | Part of the ASP.NET Core framework, runs on .NET Core, making it cross-platform (Windows, Linux, macOS).                     |
| **Performance**          | Efficient but limited by the older architecture and .NET Framework.                  | Lightweight and high-performance, optimized for modern needs with extensive support for asynchronous programming.            |
| **API Design Features**  | Supports RESTful services but lacks native support for features like versioning or response compression. | Includes built-in features like API versioning, response caching, and response compression for robust API design.            |
| **Configuration and Hosting** | Hosted in IIS, uses `web.config` for configuration.                                       | Can be hosted in IIS, Kestrel, or Docker containers. Uses JSON files, environment variables, and command-line arguments.     |
| **Dependency Injection** | Supported but relies on third-party libraries like Unity or Ninject.                  | Built-in dependency injection support, promoting loosely coupled and manageable code.                                       |
| **Middleware Support**   | No middleware pipeline; uses custom handlers and modules, which are complex to implement. | Built on a middleware pipeline for easy customization and configuration (e.g., authentication, error handling, logging).     |
| **Community and Future Support** | Part of the older .NET Framework; only receives bug fixes and security updates.           | Actively developed with new features, benefiting from Microsoft’s focus on modern ASP.NET Core architecture.                |
| **Choosing Factors**     | Suitable for legacy systems and integration with older .NET Framework-based applications. | Preferred for cross-platform needs, high-performance applications, and modern development practices.                         | 

Here are the key notes based on the given information about the ASP.NET Core Web API project structure:

### Key Folders and Files in an ASP.NET Core Web API Project:
![image](https://github.com/user-attachments/assets/f2e31b83-cd48-4151-8cd1-27c5a885270c)


1. **Connected Services**:
   - Allows easy connection to external services (e.g., Azure, Office 365, third-party REST APIs).
   - Manages configurations and client code generation for external services.

2. **Dependencies**:
   - Contains all packages and SDKs installed in the project, including:
     - **Analyzers**: Tools to check code quality and style violations.
     - **Frameworks**: Core libraries and components required by the project, such as `Microsoft.AspNetCore.App` (MVC, Razor, etc.).
     - **Packages**: External libraries for various functionalities like database access, logging, and authentication. E.g., `Swashbuckle.AspNetCore` for Swagger support.

3. **Properties**:
   - Contains `launchSettings.json`, which holds configuration settings for launching the app, such as URLs, environment variables, and profile settings (HTTP, HTTPS, IIS Express).

4. **Controllers Folder**:
   - Holds controller classes responsible for handling HTTP requests and returning responses.
   - Default example: `WeatherForecastController`.
   - Controllers are decorated with attributes like `[ApiController]` and `[Route]`.

5. **appsettings.json**:
   - Contains configuration settings like connection strings, logging settings, and custom configurations.
   - It can be overridden by environment-specific files (e.g., `appsettings.Development.json`).

6. **Program.cs**:
   - Entry point of the application where the app is configured and started.
   - Contains setup for services and middleware, including Swagger setup for API documentation.

7. **WeatherForecast.cs (Model Class)**:
   - Represents the data structure (e.g., weather information) returned by the API.
   - Can be placed in the `Models` folder or directly at the project level.

8. **MyFirstWebAPIProject.http**:
   - Used for testing HTTP requests directly from the IDE (e.g., Visual Studio or JetBrains Rider).
   - Contains HTTP requests like `GET`, `POST`, etc., which can be executed from the IDE.
   - Provides convenience for testing API endpoints without external tools like Postman.
---
### File Breakdown in `launchSettings.json`:

1. **Profiles**:
   - **HTTP Profile**: Specifies the URL and port for HTTP requests (e.g., `http://localhost:5222`).
   - **HTTPS Profile**: Specifies the URL and port for secure HTTPS requests, with SSL support.
   - **IIS Express Profile**: Configuration for running the application with IIS Express.

Here is the `launchSettings.json` file with the code comments explaining each section:

```json
{
  "profiles": {
    // HTTP Profile: Launches the app on HTTP with the specified URL
    "http": {
      "commandName": "Project",  // Runs the project directly
      "launchBrowser": true,  // Automatically opens the browser
      "launchUrl": "swagger",  // Opens the Swagger UI by default
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development"  // Sets the environment to 'Development'
      },
      "dotnetRunMessages": true,  // Shows .NET run messages
      "applicationUrl": "http://localhost:5222"  // Application URL for HTTP
    },
    // HTTPS Profile: Launches the app with HTTPS for secure communication
    "https": {
      "commandName": "Project",  // Runs the project directly
      "launchBrowser": true,  // Automatically opens the browser
      "launchUrl": "swagger",  // Opens the Swagger UI by default
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development"  // Sets the environment to 'Development'
      },
      "dotnetRunMessages": true,  // Shows .NET run messages
      "applicationUrl": "https://localhost:7237;http://localhost:5222"  // Application URLs for HTTPS and HTTP
    },
    // IIS Express Profile: Launches the app using IIS Express for local development
    "IIS Express": {
      "commandName": "IISExpress",  // Uses IIS Express to launch the app
      "launchBrowser": true,  // Automatically opens the browser
      "launchUrl": "swagger",  // Opens the Swagger UI by default
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development"  // Sets the environment to 'Development'
      }
    }
  },
  "$schema": "http://json.schemastore.org/launchsettings.json",  // Defines the schema for this file
  // IIS Express settings: Configures IIS Express for local development
  "iisSettings": {
    "windowsAuthentication": false,  // Disables Windows Authentication
    "anonymousAuthentication": true,  // Enables anonymous authentication
    "iisExpress": {
      "applicationUrl": "http://localhost:1064",  // URL for IIS Express
      "sslPort": 44312  // SSL Port for secure communication in IIS Express
    }
  }
}
```

### Key Points:
- **Profiles**:
  - `http`: Launches on HTTP at `http://localhost:5222`.
  - `https`: Launches on HTTPS at `https://localhost:7237` and HTTP at `http://localhost:5222`.
  - `IIS Express`: Uses IIS Express on `http://localhost:1064`.
  
- **Environment Variables**: All profiles set `ASPNETCORE_ENVIRONMENT` to "Development" for local development.
  
- **IIS Settings**: Configures IIS Express with anonymous authentication enabled and SSL port set to `44312`.

---
### Advantages of `.http` File:
- **Convenience**: Test API endpoints directly from the IDE.
- **Version Control**: Can be checked into source control for collaboration.
- **Documentation**: Serves as documentation for API endpoints.

Here are the summarized notes for the article on **Controllers in ASP.NET Core Web API**:

---

### **What are Controllers in ASP.NET Core Web API?**
- **Definition:** Controllers handle incoming HTTP requests and generate responses (usually in JSON or XML format).
- **Roles:**
  1. **Request Handling:** Match HTTP requests to action methods.
  2. **Data Processing:** Interact with models and implement logic.
  3. **Response Generation:** Return data, status codes, or error messages.

---

### **Adding a Controller Class**
1. **Naming Convention:**
   - Must end with the "Controller" suffix (e.g., `EmployeeController`).
2. **Inheritance:**
   - Controllers typically inherit from `ControllerBase` for Web API projects.
3. **Location:**
   - Place controllers in the `Controllers` folder in the project root.

---

### **Modifying Controllers**
- Use routing attributes like `[Route("api/[controller]")]` to define URL access points.
- **Ambiguous Match Exception:**
  - Avoid having multiple methods with the same HTTP verb and route. Use unique identifiers in the route attribute (e.g., `[Route("api/[controller]/[action]")]`).

---

### **Key Features of Controllers**
1. **Routing Attributes:** Use `[Route]`, `[HttpGet]`, `[HttpPost]`, etc., to define routes.
2. **Action Methods:** Handle specific HTTP requests (GET, POST, etc.) with methods like `Ok()`, `NotFound()`.
3. **Parameter Binding:** Automatically bind parameters from the route, query string, or request body.
4. **Response Handling:**
   - Use `IActionResult` or `ActionResult<T>` for flexible response types.

---

### **[ApiController] Attribute**
- **Enhancements:**
  1. Automatic 400 responses for invalid models.
  2. Requires attribute routing.
  3. Simplifies parameter binding based on HTTP methods.
  4. Standardized `ProblemDetails` for error responses.
  5. Streamlined handling of multipart/form-data requests.

---

### **Difference Between `ControllerBase` and `Controller`**
- **ControllerBase:**
  - Lightweight, used for Web APIs without views.
  - Offers core MVC features like action methods, routing, model binding, and HTTP responses.
  - No support for rendering views.
- **Controller:**
  - Inherits `ControllerBase` but adds view rendering capabilities.
  - Suitable for MVC applications that require HTML views.

#### **When to Choose:**
- Use `ControllerBase` for APIs (lightweight, JSON/XML-focused).
- Use `Controller` for MVC applications (supports Razor views).

---

### **What Are Models in ASP.NET Core Web API?**
- **Definition**: Models are classes representing the data structure of an application. They define the schema for data handled by the Web API and often encapsulate business logic related to that data.
- **Purpose**: 
  - Transfer data between client and server (Data Transfer Objects - DTOs).
  - Define validation rules.
  - Provide a structured format for both incoming and outgoing data.
  
---

### **Key Characteristics of Models**
1. **Data Annotations**: 
   - Use attributes like `[Required]`, `[StringLength]`, `[EmailAddress]`, etc., from the `System.ComponentModel.DataAnnotations` namespace to enforce validation rules.
2. **Data Transfer Objects (DTOs)**:
   - Customize and optimize the data exposed to clients.
   - Hide properties that shouldn't be shared over the API.
3. **Validation**: 
   - Models ensure data integrity by validating input data before processing.
   - Invalid data results in validation errors returned to the client.
4. **Relationships**: 
   - Models can represent relationships, such as one-to-many (e.g., `Order` and `OrderDetails`).

---

### **Creating and Using Models**
1. **Location**: Models are often created in the `Models` folder for organization, but they can exist in any folder or class library.
   
2. **Example Models**:
   - **Product Model**: A simple class defining `Id`, `Name`, `Price`, and `Category`.
   - **User Model with Annotations**: Enforces rules like required fields and string length.
   - **Order and OrderDetails Models**: Demonstrates a one-to-many relationship.
   - **Employee Model with Enumeration**: Shows how enums can be integrated into models.

3. **Usage in Controllers**:
   - Models are used in controllers to:
     - Bind incoming HTTP request data.
     - Return structured data in HTTP responses.
   - Example: `ProductsController` handles CRUD operations using the `Product` model.

---

### **CRUD Operations in Controllers**
- **GET**: Retrieve all products or a specific product by ID.
- **POST**: Create a new product with input data.
- **PUT**: Update an existing product's details.
- **DELETE**: Remove a product by ID.

Each operation uses models to:
- Parse incoming data (e.g., POST, PUT).
- Format outgoing responses (e.g., GET).
- Validate data integrity (e.g., ensure `Id` matches).

---

### **Testing APIs**
- **Testing Tools**:
  - Use Postman, Swagger, or Visual Studio's `.http` file to test API functionality.
- **Sample HTTP Requests**:
  - Include headers (`Content-Type`, `Accept`) and JSON payloads to interact with the API endpoints.
  
---

### **Specialized Models**
1. **With Data Annotations**:
   - Example: `User` model ensures `FirstName`, `LastName`, and `Email` adhere to specific validation rules.
2. **With Relationships**:
   - Example: `Order` model has a collection of `OrderDetails`, demonstrating one-to-many relationships.
3. **With Enumerations**:
   - Example: `Employee` model uses a `Department` enum to categorize employees.

---

### **Benefits of Models**
- **Data Validation**: Automates validation and prevents invalid data from being processed.
- **Maintainability**: Ensures clean separation of concerns.
- **Reusability**: Models can be reused across different parts of the application.
- **Optimization**: DTOs help reduce unnecessary data transfer, improving performance.

---

### **Key Takeaways**
- Models form the backbone of data handling in ASP.NET Core Web API.
- By combining models with validation, DTOs, and relationships, APIs can ensure data consistency, optimize performance, and facilitate communication between client and server.
- Testing tools and well-structured models streamline API development and ensure reliability.

---
### **Key HTTP Response Methods in ASP.NET Core Web API**
| **HTTP Method** | **Response Method**   | **HTTP Status Code** | **Description**                                                                 |
|------------------|-----------------------|-----------------------|---------------------------------------------------------------------------------|
| **GET**          | `Ok`                 | 200 OK               | Successfully retrieves data.                                                   |
| **GET**          | `NotFound`           | 404 Not Found        | Resource with the specified ID does not exist.                                 |
| **POST**         | `CreatedAtAction`    | 201 Created          | Successfully creates a new resource and includes its location in the header.   |
| **PUT**          | `NoContent`          | 204 No Content       | Successfully updates a resource without returning any data.                    |
| **PUT**          | `BadRequest`         | 400 Bad Request      | Input data does not meet the expected format or contains errors.               |
| **DELETE**       | `NoContent`          | 204 No Content       | Successfully deletes a resource without returning any data.                    |
| **DELETE**       | `NotFound`           | 404 Not Found        | Resource to delete does not exist.                                             |

--- 
</details>

## **Routing in ASP.NET Core Web API**
<details>
<summary> ---Expand--- </summary>

Routing in ASP.NET Core Web API maps incoming HTTP requests to specific controller action methods. It determines how URLs correlate to actions and allows for efficient request handling.

### **Two Types of Routing**
1. **Conventional Routing**:
   - Defined globally in the `Program.cs` file.
   - Routes follow a predictable pattern (e.g., `api/{controller}/{action}/{id?}`).
   - Suitable for simple or common routing structures.
   - Example:
     ```csharp
     app.MapControllerRoute(
         name: "default",
         pattern: "api/{controller}/{action}/{id?}");
     ```

2. **Attribute Routing**:
   - Defined directly on controllers or action methods using attributes.
   - Offers flexibility for defining custom or complex URL patterns.
   - Supports HTTP Verb attributes like `[HttpGet]`, `[HttpPost]`, `[HttpPut]`, etc.
   - Example:
     ```csharp
     [Route("Emp/All")]
     [HttpGet]
     public string GetAllEmployees()
     {
         return "Response from GetAllEmployees Method";
     }
     ```

### **Examples of Attribute Routing**
- **Basic Route Definition**:
   ```csharp
   [Route("Emp/ById/{Id}")]
   [HttpGet]
   public string GetEmployeeById(int Id)
   {
       return $"Response from GetEmployeeById Method Id: {Id}";
   }
   ```
   Access: `/Emp/ById/102`

- **HTTP Verb Attributes**:
   ```csharp
   [HttpGet("api/products")]
   public IActionResult GetAllProducts()
   {
       return Ok(new List<string> { "Product1", "Product2" });
   }
   ```

### **How Routing Works**
1. **Route Table Creation**:
   - When `app.MapControllers()` is called, ASP.NET Core scans controllers and routes to create a route table.
   - The route table maps URL patterns to controller actions.

2. **Middleware**:
   - **UseRouting** middleware determines the endpoint based on the request URL and method.
   - **UseEndpoints** middleware executes the identified action method.

3. **Mapping Requests**:
   - Incoming requests are matched against the route table, and the action method is executed.

### **Combining Routing Approaches**
- You can use both conventional and attribute-based routing in the same application. Attribute routing takes precedence for actions decorated with route attributes.

   Example:
   ```csharp
   [Route("Emp/All")]
   [HttpGet]
   public string GetAllEmployees() { ... }

   [HttpGet]
   public string GetEmployeeById(int Id) { ... }
   ```
   - `/Emp/All` → Attribute Routing.
   - `/api/employee/GetEmployeeById/102` → Conventional Routing.

### **When to Use Which**
- **Conventional Routing**:
  - Best for simple or uniform route patterns.
  - Ideal for small or medium applications.
- **Attribute Routing**:
  - Suitable for APIs and large applications with complex or highly customized routes.

---

### **Route Parameters in ASP.NET Core Web API**
- **Purpose**: Route parameters are used to include mandatory dynamic values directly in the URL path, such as entity identifiers or key attributes.
- **Definition**: Use curly braces `{}` in the route template and match these with method parameters. Example:
  ```csharp
  [Route("Employee/{Id}")]
  [HttpGet]
  public string GetEmployeeById(int Id)
  {
      return $"Return Employee Details : {Id}";
  }
  ```
  - **Example Usage**: `/Employee/100` retrieves the employee with ID `100`.

#### **Passing Multiple Route Parameters**
You can define multiple dynamic values in the route. For example:
```csharp
[Route("Employee/Gender/{Gender}/City/{CityId}")]
[HttpGet]
public string GetEmployeesByGenderAndCity(string Gender, int CityId)
{
    return $"Return Employees with Gender : {Gender}, City : {CityId}";
}
```
- **Example Usage**: `/Employee/Gender/Male/City/10` retrieves employees based on gender `Male` and city `10`.

---

### **Query Strings in ASP.NET Core Web API**
- **Purpose**: Query strings are used to pass optional, additional information in the URL. They are often used for filtering, sorting, and other flexible parameters.
- **Syntax**: Key-value pairs are appended to the URL after a `?`, separated by `&`. Example:
  ```csharp
  [Route("Employee/Search")]
  [HttpGet]
  public string SearchEmployees(string? Department, string? Gender, string? City = null)
  {
      return $"Return Employees with Department : {Department}, Gender : {Gender}, City : {City}";
  }
  ```
  - **Example Usage**:
    - `/Employee/Search?Department=IT` filters by department.
    - `/Employee/Search?Gender=Male&City=NewYork` filters by gender and city.

#### **Using Query Strings with Model Binding**
Complex query strings can be mapped to an object model using the `[FromQuery]` attribute. Example:
```csharp
public class EmployeeSearch
{
    public string? Department { get; set; }
    public string? Gender { get; set; }
    public string? City { get; set; }
}

[Route("Employee/Search")]
[HttpGet]
public string SearchEmployees([FromQuery] EmployeeSearch employeeSearch)
{
    return $"Return Employees with Department : {employeeSearch.Department}, Gender : {employeeSearch.Gender}, City : {employeeSearch.City}";
}
```
This allows passing multiple parameters like `/Employee/Search?Gender=Male&City=London`.

---

### **Combining Route Parameters and Query Strings**
It is possible to mix route parameters and query strings. Example:
```csharp
[Route("Employee/{Gender?}")]
[HttpGet]
public string GetEmployeesByGenderAndCity(string? Gender, int? CityId, string? Department)
{
    return $"Return Employees with Gender: {Gender}, City: {CityId}, Department: {Department}";
}
```
- **Example Usage**: `/Employee/Male?Department=HR&CityId=100` combines the gender from the route and other filters as query strings.

---

### **Key Differences Between Route Parameters and Query Strings**
| **Aspect**         | **Route Parameters**                             | **Query Strings**                                   |
|---------------------|--------------------------------------------------|----------------------------------------------------|
| **Position**        | Part of the URL path (e.g., `/Employee/100`).    | Appended after `?` in the URL (e.g., `?City=NY`).  |
| **Optionality**     | Typically mandatory.                            | Optional and flexible.                             |
| **Purpose**         | Identify specific resources.                    | Provide additional information or filtering.       |
| **Use Cases**       | Entity IDs, resource-specific paths.            | Filters, sorting, optional configurations.         |

---

### **Accessing Query Strings Directly from `HttpContext`**
If you prefer not to use method parameters, query strings can be accessed directly:
```csharp
[Route("Employee/Search")]
[HttpGet]
public string SearchEmployees()
{
    var Department = HttpContext.Request.Query["Department"].ToString();
    var Gender = HttpContext.Request.Query["Gender"].ToString();
    return $"Return Employees with Department : {Department}, Gender : {Gender}";
}
```

---

### **Best Practices**
1. Use **route parameters** for essential, non-optional values (e.g., resource identifiers).
2. Use **query strings** for optional or additional filtering criteria.
3. For complex query string scenarios, leverage **model binding** with `[FromQuery]`.
4. Ensure clear, consistent API design by following RESTful principles.

--- 

### **Scenarios for Multiple URLs for a Single Resource**
Here are some scenarios where setting up multiple URLs for a single resource is beneficial:

a) API Versioning
Different URLs for different API versions:

```csharp
[Route("api/v1/resource")]
[Route("api/v2/resource")]
```
b) Backward Compatibility
When renaming an endpoint or modifying its structure, you can keep the old route alongside the new route:
```csharp
[Route("api/legacy-resource")]
[Route("api/resource")]
```
c) Supporting Alternate Naming Conventions
If different client applications use different naming conventions:
```csharp
[Route("employees")]
[Route("workers")]
```
---
### **Token Replacement in ASP.NET Core Web API Routing**

### **Common Tokens**:
- **`[controller]`**: Replaces with the controller name.
- **`[action]`**: Replaces with the action method name.
- **`{id}`**: Represents a route parameter.

---

### **Example Without Token Replacement**:
Explicit routes for each action:

```csharp
[ApiController]
public class EmployeeController : ControllerBase
{
    [Route("Employee/GetAllEmployees")]
    [HttpGet]
    public string GetAllEmployees() => "All Employees";

    [Route("Employee/GetAllDepartment")]
    [HttpGet]
    public string GetAllDepartment() => "All Departments";
}
```

---

### **Using Token Replacement**:
With tokens like `[controller]` and `[action]`, you can simplify routing:

```csharp
[ApiController]
[Route("[controller]")]
public class EmployeeController : ControllerBase
{
    [Route("[action]")]
    [HttpGet]
    public string GetAllEmployees() => "All Employees";

    [Route("[action]")]
    [HttpGet]
    public string GetAllDepartment() => "All Departments";
}
```

**Resulting URLs**:
- `/Employee/GetAllEmployees`
- `/Employee/GetAllDepartment`

---

### **Apply Token Replacement at Controller Level**:
Instead of repeating `[Route("[action]")]` on each method, apply the token at the controller level:

```csharp
[ApiController]
[Route("[controller]/[action]")]
public class EmployeeController : ControllerBase
{
    [HttpGet]
    public string GetAllEmployees() => "All Employees";

    [HttpGet]
    public string GetAllDepartment() => "All Departments";
}
```

---

### **Dynamic Token Replacement**:
You can also use dynamic parameters:

```csharp
[ApiController]
[Route("[controller]/[action]")]
public class EmployeeController : ControllerBase
{
    [HttpGet]
    [Route("{id}")]
    public string GetEmployeeById(int id) => $"Employee ID: {id}";
}
```

**Resulting URL**:
- `/Employee/GetEmployeeById/10` (for `id = 10`)

---

### **Benefits**:
- **Clean & Consistent Routes**: Automatically adjusts for controller and action name changes.
- **Dynamic URLs**: Supports parameters like `{id}`.
- **Less Repetition**: Reduces code duplication by defining common routes at the controller level.

---
### **Route Constraints**
Route Constraints in ASP.NET Core Web API allow developers to define rules that restrict the values of parameters in routes. These constraints help ensure that the API only processes valid requests and routes them to the correct action methods. They improve routing accuracy, reduce unnecessary processing, and enhance security by validating requests before they reach the action methods.

### Types of Route Constraints in ASP.NET Core Web API:

1. **Type Constraints**:
   - Ensure parameters are of a specific type.
   - Common types include `int`, `decimal`, `bool`, `float`, `datetime`, etc.
   - Example: `[Route("{EmployeeId:int}")]` ensures the `EmployeeId` parameter is an integer.

2. **Min/Max Constraints**:
   - Define the minimum (`min`) or maximum (`max`) values that a parameter can have.
   - Example: `[Route("{EmployeeId:int:min(1000)}")]` ensures the `EmployeeId` is greater than or equal to 1000.

3. **Range Constraint**:
   - Specifies both a minimum and maximum range for numeric values.
   - Example: `[Route("{EmployeeId:int:range(100,1000)}")]` ensures the `EmployeeId` is between 100 and 1000.

4. **Alpha Constraint**:
   - Restricts a parameter to only alphabetic characters (a-z, A-Z).
   - Example: `[Route("{EmployeeName:alpha}")]` ensures the `EmployeeName` consists only of letters.

5. **MinLength/MaxLength/Length Constraints**:
   - Enforces constraints on the length of string parameters.
   - Example: `[Route("{EmployeeName:alpha:minlength(5)}")]` ensures `EmployeeName` is at least 5 characters long.
   - Example: `[Route("{EmployeeName:alpha:maxlength(10)}")]` ensures `EmployeeName` is no longer than 10 characters.
   - Example: `[Route("{EmployeeName:alpha:length(5)}")]` ensures `EmployeeName` is exactly 5 characters long.

6. **Regex Constraint**:
   - Uses a regular expression to validate the parameter against a specific pattern.
   - Example: `[Route("{EmployeeName:regex(a(b|c))}")]` ensures that `EmployeeName` starts with "a" followed by either "b" or "c".

### Example of Route Constraints in Action:
```csharp
[Route("{EmployeeId:int:min(1000):max(10000)}")]
[HttpGet]
public string GetEmployeeDetails(int EmployeeId)
{
    return $"Employee ID: {EmployeeId}";
}
```
In this example:
- The route accepts only integers (`int`).
- The `EmployeeId` must be between 1000 and 10000 (`min(1000):max(10000)`).

### Benefits of Using Route Constraints:
1. **Validation at the Routing Level**:
   - Validates the parameters before they reach the action method, preventing invalid requests from processing further.
   
2. **Improved Security**:
   - Helps mitigate security issues by ensuring only properly formatted and safe inputs are allowed.
   
3. **Precise URL Matching**:
   - Allows fine-grained control over which requests match specific actions, improving the accuracy of route handling.

4. **Better Error Handling**:
   - Route constraints ensure that only valid requests hit the corresponding action methods, leading to fewer errors and less need for additional validation inside the action methods.

5. **Simplified Code**:
   - By specifying route constraints directly in the route attributes, developers can avoid writing extra validation code in the controller methods.


</details>


## **Model Binding**
<details>
<summary> ---Expand--- </summary>

### **What is Model Binding in ASP.NET Core Web API?**
- **Model Binding** is the process where ASP.NET Core maps HTTP request data to action method parameters.
- It extracts and converts data from sources like:
  - Query strings
  - Form data
  - Route data
  - Request bodies
- This allows developers to work with strongly-typed .NET objects instead of parsing request data manually.

---

### **Why is Model Binding Important?**
1. **Simplifies Data Access**: Automates the process of extracting and converting data.
2. **Supports Multiple Sources**: Works with query strings, form data, JSON bodies, headers, etc.
3. **Strong Typing**: Converts data into strongly-typed objects for validation and easier use.
4. **Validation Integration**: Works seamlessly with validation attributes to ensure data integrity.

---

### **How HTTP Verbs Map to Action Methods?**
- **Routing Attributes**: Attributes like `[HttpGet]`, `[HttpPost]`, etc., specify the HTTP method for an action.
- **Route Templates**: URLs defined in `Route` attributes or configuration guide request-to-method mapping.

---

### **Model Binding Techniques**
- **[FromBody]**: Binds from the request body (e.g., JSON).
- **[FromForm]**: Binds from posted form fields.
- **[FromQuery]**: Binds from the query string.
- **[FromRoute]**: Binds from route data.
- **[FromHeader]**: Binds from HTTP headers.

---

### **Types of Model Binders**
1. **Simple Types Binder**: Handles basic types (e.g., `int`, `string`).
2. **Complex Types Binder**: Binds complex types using JSON or XML serialization.
3. **Custom Binders**: For advanced scenarios requiring custom logic (via `IModelBinder`).

---

### **Built-in Model Binders**
- `QueryStringModelBinder`: For query strings.
- `RouteDataModelBinder`: For route data.
- `FormModelBinder`: For form data.
- `BodyModelBinder`: For request body data.
- `HeaderModelBinder`: For HTTP headers.

---

### **Value Providers**
- Fetch data from specific parts of the HTTP request.
  - **QueryStringValueProvider**: Data from the URL's query string.
  - **FormValueProvider**: Data from `application/x-www-form-urlencoded` or `multipart/form-data`.
  - **RouteDataValueProvider**: Data from route parameters.
  - **HeaderValueCollectionProvider**: Data from HTTP headers.
  - **JsonBodyValueProvider**: Data from JSON-formatted request bodies.

---

### **Error Handling in Model Binding**
1. **Validation with ModelState**:
   - Use `ModelState.IsValid` to check for errors.
   - Return **BadRequest** with errors if invalid.
2. **NotFound Responses**:
   - Return **404 Not Found** when requested data isn’t available.
3. **Custom Error Responses**:
   - Tailor error responses as per application requirements.

---

### **Example: Product Management API**
- **Model**: `Product` class with validation attributes (e.g., `[Required]`, `[Range]`).
- **Controller**: `ProductsController` with methods demonstrating model binding:
  - **GetProduct**: `[FromRoute]` to bind ID.
  - **GetProducts**: `[FromQuery]` to filter by category.
  - **CreateProduct**: `[FromBody]` for JSON request body.
  - **UpdateProduct**: Combines `[FromRoute]` and `[FromBody]`.
  - **DeleteProduct**: `[FromRoute]` for ID.
  - **GetProductFromHeader**: `[FromHeader]` to extract from custom headers.
  - **UploadFile**: `[FromForm]` to handle file uploads.

---

### **How Model Binding Works?**
1. **Routing**: Identifies the controller and action method.
2. **Source Identification**: Determines data source (e.g., query string, form, body).
3. **Type Matching**: Matches data type with the target parameter or model.
4. **Conversion**: Converts source data into the target type.
5. **Data Assignment**: Assigns the converted data to method parameters or model properties.

---

</details>
