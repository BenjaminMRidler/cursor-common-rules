# C# Coding Standards

## 🎯 Purpose
This file contains common C# coding standards and best practices that ensure consistency, readability, and maintainability across all C# projects.

## 📋 Naming Conventions

### **General Naming Rules**
- **Use PascalCase** for public members, types, and namespaces
- **Use camelCase** for private fields, local variables, and parameters
- **Use UPPER_CASE** for constants and static readonly fields
- **Use descriptive names** that clearly indicate purpose and intent
- **Avoid abbreviations** unless they are widely understood

### **Specific Naming Patterns**
- **Classes and Structs**: `PascalCase` (e.g., `UserService`, `DatabaseConnection`)
- **Interfaces**: `IPascalCase` (e.g., `IUserService`, `IDatabaseConnection`)
- **Methods**: `PascalCase` (e.g., `GetUserById`, `SaveUserData`)
- **Properties**: `PascalCase` (e.g., `UserName`, `IsActive`)
- **Private Fields**: `camelCase` with underscore prefix (e.g., `_userName`, `_isActive`)
- **Constants**: `UPPER_CASE` (e.g., `MAX_RETRY_COUNT`, `DEFAULT_TIMEOUT`)

## 🏗️ Code Organization

### **File Structure**
- **One class per file** - file name should match class name
- **Namespace organization** - group related classes in logical namespaces
- **Using statements** - organize alphabetically and group by source
- **Region usage** - use regions sparingly, prefer logical organization

### **Class Organization**
```csharp
public class ExampleService
{
    // Constants
    private const int MaxRetries = 3;
    
    // Private fields
    private readonly ILogger<ExampleService> _logger;
    private readonly IConfiguration _configuration;
    
    // Constructor
    public ExampleService(ILogger<ExampleService> logger, IConfiguration configuration)
    {
        _logger = logger;
        _configuration = configuration;
    }
    
    // Public methods
    public async Task<Result> ProcessDataAsync(DataRequest request)
    {
        // Implementation
    }
    
    // Private methods
    private async Task<DataResult> ValidateDataAsync(DataRequest request)
    {
        // Implementation
    }
}
```

## 🔧 Language Features

### **Async/Await Patterns**
- **ALWAYS use async/await** for database operations and external service calls
- **ALWAYS return Task or Task<T>** from async methods
- **ALWAYS use ConfigureAwait(false)** for library code
- **ALWAYS handle exceptions** in async methods appropriately

```csharp
public async Task<User> GetUserAsync(int userId)
{
    try
    {
        var user = await _userRepository.GetByIdAsync(userId).ConfigureAwait(false);
        return user ?? throw new UserNotFoundException(userId);
    }
    catch (Exception ex)
    {
        _logger.LogError(ex, "Failed to get user {UserId}", userId);
        throw;
    }
}
```

### **Exception Handling**
- **ALWAYS catch specific exceptions** rather than generic Exception
- **ALWAYS log exceptions** with appropriate context
- **ALWAYS re-throw exceptions** when you cannot handle them
- **ALWAYS use meaningful exception types** for business logic errors

```csharp
try
{
    var result = await _externalService.CallAsync();
    return result;
}
catch (HttpRequestException ex) when (ex.StatusCode == HttpStatusCode.NotFound)
{
    _logger.LogWarning("External service returned 404 for request");
    return null;
}
catch (HttpRequestException ex)
{
    _logger.LogError(ex, "External service call failed");
    throw new ServiceUnavailableException("External service is unavailable", ex);
}
```

## 📚 SOLID Principles

### **Single Responsibility Principle**
- **Each class should have one reason to change**
- **Keep methods focused and cohesive**
- **Extract complex logic into separate classes**

### **Open/Closed Principle**
- **Open for extension, closed for modification**
- **Use interfaces and abstract classes**
- **Implement new features through composition**

### **Liskov Substitution Principle**
- **Derived classes must be substitutable for base classes**
- **Maintain behavioral contracts**
- **Don't violate base class assumptions**

### **Interface Segregation Principle**
- **Keep interfaces focused and specific**
- **Don't force clients to depend on methods they don't use**
- **Split large interfaces into smaller, focused ones**

### **Dependency Inversion Principle**
- **Depend on abstractions, not concretions**
- **Use dependency injection**
- **Invert control of dependencies**

## 🧪 Testing Standards

### **Test Naming Convention**
- **Use descriptive test names** that explain the scenario
- **Follow pattern**: `MethodName_Scenario_ExpectedResult`
- **Use underscores to separate parts** of the test name

```csharp
[Fact]
public async Task GetUserAsync_ValidUserId_ReturnsUser()
{
    // Arrange
    var userId = 1;
    var expectedUser = new User { Id = userId, Name = "Test User" };
    _userRepository.Setup(r => r.GetByIdAsync(userId)).ReturnsAsync(expectedUser);
    
    // Act
    var result = await _userService.GetUserAsync(userId);
    
    // Assert
    Assert.Equal(expectedUser, result);
}

[Fact]
public async Task GetUserAsync_InvalidUserId_ThrowsUserNotFoundException()
{
    // Arrange
    var userId = -1;
    _userRepository.Setup(r => r.GetByIdAsync(userId)).ReturnsAsync((User)null);
    
    // Act & Assert
    await Assert.ThrowsAsync<UserNotFoundException>(() => 
        _userService.GetUserAsync(userId));
}
```

### **Test Organization**
- **Use AAA pattern**: Arrange, Act, Assert
- **Mock external dependencies** using appropriate mocking framework
- **Test both positive and negative** scenarios
- **Test edge cases** and boundary conditions

## 📝 Documentation

### **XML Documentation**
- **ALWAYS add XML documentation** to public APIs
- **Document parameters, return values, and exceptions**
- **Include usage examples** for complex methods
- **Document assumptions and limitations**

```csharp
/// <summary>
/// Retrieves a user by their unique identifier.
/// </summary>
/// <param name="userId">The unique identifier of the user to retrieve.</param>
/// <returns>
/// The user if found; otherwise, null.
/// </returns>
/// <exception cref="ArgumentOutOfRangeException">
/// Thrown when <paramref name="userId"/> is less than or equal to zero.
/// </exception>
/// <exception cref="UserNotFoundException">
/// Thrown when no user exists with the specified <paramref name="userId"/>.
/// </exception>
public async Task<User> GetUserAsync(int userId)
{
    // Implementation
}
```

## 🔒 Security Considerations

### **Input Validation**
- **ALWAYS validate input parameters** at method boundaries
- **Use parameter validation attributes** when appropriate
- **Sanitize user input** before processing
- **Validate file paths and URLs** to prevent path traversal attacks

### **Authentication and Authorization**
- **ALWAYS verify user permissions** before performing operations
- **Use secure authentication mechanisms**
- **Implement proper session management**
- **Log security-related events** appropriately

## 📊 Performance Guidelines

### **Memory Management**
- **Use value types** for small, frequently used data
- **Implement IDisposable** for classes that manage unmanaged resources
- **Use object pooling** for frequently created/destroyed objects
- **Avoid unnecessary allocations** in hot paths

### **Async Patterns**
- **Use async/await** for I/O-bound operations
- **Use Task.Run** sparingly for CPU-bound operations
- **Configure await** appropriately for library vs. application code
- **Handle cancellation** using CancellationToken

## 📝 Changelog

### [2025-01-27] - Initial Release
- **Added**: Naming conventions and code organization standards
- **Added**: Async/await patterns and exception handling
- **Added**: SOLID principles implementation guidelines
- **Added**: Testing standards and naming conventions
- **Added**: XML documentation requirements
- **Added**: Security considerations and performance guidelines
