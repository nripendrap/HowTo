## Add config file in dotnet core console application

1. Add IConfiguration and ConfigurationBuilder NuGet packages.
```
Install-Package Microsoft.Extensions.Configuration
Install-Package Microsoft.Extensions.Configuration.Json
Install-Package Microsoft.Extensions.Configuration.CommandLine
Install-Package Microsoft.Extensions.Configuration.EnvironmentVariables 
Install-Package Microsoft.Extensions.Configuration.Binder
```

2. Add a json configuration file called appsettings.json
```
IConfiguration Configuration = new ConfigurationBuilder()
    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
    .AddEnvironmentVariables()
    .AddCommandLine(args)
    .Build();
```

3. Update appsettings.json file "Copy to Output Directory" property so that the application is able to access it when published
    1. Select and right click appsettings.json file
    2. Select Properties
    3. Under Advanced -> Copy to Output Directory 
    4. Select Copy always/Copy if newer

## dotnet ef ... Could not execute because the specified command or file was not found

```
PS>dotnet ef migrations add InitialCreate 
Could not execute because the specified command or file was not found. dotnet ef ... Could not execute because the specified command or file was not found. 
Possible reasons for this include: * You misspelled a built-in dotnet command. * You intended to execute a .NET program, but dotnet-ef does not exist. * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.
```

Install dotnet-ef as a global tool 
```
dotnet tool install --global dotnet-ef
```

## Dotnet core MVC Page Not refreshing after changes

1. Add Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation NuGet package to the project
2. Add the following in Startup.cs:
```
services.AddControllersWithViews().AddRazorRuntimeCompilation();
```

## Prevent favicon.ico requests
__Issue__ \
When made a http request to the web page from the browser, it also make request to favicon.ico, though I don't favicon.ico in the web page.
__Soln__ \
Add following line to the &lt;head&gt; section
```
<link rel="icon" href="data:,">
```

## dotnet CLI commands
__List installed templates__
```
dotnet new --list
```
__Create solution file__
```
dotnet new sln
```
__Add project to the solution__
```
dotnet sln add .\src\Cafedulait.IdentityServer4\Cafedulait.IdentityServer4.csproj
```
