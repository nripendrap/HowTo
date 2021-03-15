AWS Lambda Using AWS Toolkit for Visual Studio

1. Open Microsoft Visual Studio
2. File -> New -> Project
3. Choose AWS Lambda Project (.NET Core - C#)
4. Choose Next button
5. Name: QRCodeAWSLambda
6. Enter desired location
7. Choose Create button
8. On Select Blueprint window, choose the Simple Application Load Balance Function
9. Choose Finish button
10. Select Tools -> NuGet Package Manager -> Manage NuGet Packages for Solution
11. Choose Browse tab
12. Search QRCoder
13. Select QRCoder from the list and Install.



   
Issue 
https://github.com/aws/aws-lambda-dotnet/issues/516


## Application Load Balancer Path Based Routing


## DI in AWS Lambda
1. Add <code>Microsoft.Extensions.DependencyInjection</code> NuGet package to the project.
2. Add a ```ConfigureServices``` function that accepts an ```IServiceCollection``` and uses it to register services with the .NET Core dependency injection system.
```
private void ConfigureServices(IServiceCollection services) {
    // ToDo: Get service from DI system
}
```
2. Create a constructor
```
public Function()
{
    // Set up Dependency Injection
    var serviceCollection = new ServiceCollection();
    ConfigureServices(serviceCollection);
    var serviceProvider = serviceCollection.BuildServiceProvider();

    // TODO: Get Service from DI system
}
```
4. Add configuration code
    - Microsoft.Extensions.Configuration
    - Microsoft.Extensions.Configuration.EnvironmentVariables
    - Microsoft.Extensions.Configuration.FileExtensions
    - Microsoft.Extensions.Configuration.Json
5. Create IConfigurationService interface with a GetConfiguration method that returns an IConfiguration.
```
public interface IConfigurationService {
    IConfiguration Configuration { get; }
}
```
6. Implement IConfigurationService interface
```
public class ConfigurationService : IConfigurationService
{
    public IConfiguration Configuration => new ConfigurationBuilder()
            .SetBasePath(Directory.GetCurrentDirectory())
            .AddJsonFile("appsettings.json", optional: false, reloadOnChange: true)
            .Build();
    
}
```
7. Add appsettings.json file, and set its __Copy to Output Directory__ property to __Copy always__
    Right click appsettings.json file > select Properties. It is under Advanced.
8. Register <code>ConfigurationService</code> with the DI system inside the <code>ConfigurationServices</code> method of the <code>Function</code> class
```
private void ConfigureServices(IServiceCollection services)
{
    // Register services with DI system
    serviceCollection.AddTransient<IConfigurationService, ConfigurationService>();
}
```
9. Edit the <code>Function</code> class constructor to get <code>IConfigurationService</code> from the DI service provider and set a read-only <code>ConfigService</code> property on the class.
```
// Configuration Service
public IConfigurationService ConfigService { get; }

public Function()
{
    // Set up Dependency Injection
    var serviceCollection = new ServiceCollection();
    ConfigureServices(serviceCollection);
    var serviceProvider = serviceCollection.BuildServiceProvider();

    // Get Configuration Service from DI system
    ConfigService = serviceProvider.GetService<IConfigurationService>();
}
```
10. Add code to the FunctionHandler method to get a value from the ConfigService using the input parameter as a key.
```
public string FunctionHandler(string input, ILambdaContext context)
{
    // Get config setting using input as a key
    return ConfigService.GetConfiguration()[input] ?? "None";
}
```

###### Reference
1.  https://blog.tonysneed.com/2018/12/16/add-net-core-di-and-config-goodness-to-aws-lambda-functions/
