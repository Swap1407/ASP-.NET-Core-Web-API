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
