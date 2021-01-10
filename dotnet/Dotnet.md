Configuration in dotnet core console application
----------------------------------------

IConfiguration and ConfigurationBuilder are needed.


```
Install-Package Microsoft.Extensions.Configuration
Install-Package Microsoft.Extensions.Configuration.Json
Install-Package Microsoft.Extensions.Configuration.CommandLine
Install-Package Microsoft.Extensions.Configuration.EnvironmentVariables 
Install-Package Microsoft.Extensions.Configuration.Binder
```

Add a json configuration file called appsettings.json

```
IConfiguration Configuration = new ConfigurationBuilder()
    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
    .AddEnvironmentVariables()
    .AddCommandLine(args)
    .Build();
```

Adding appsettings.json file to dotnet core console app
---------------------------------------------

Select and right click appsettings.json file
Select Properties
Under Advanced -> Copy to Output Directory 
Select Copy always/Copy if newer



dotnet ef ...
Could not execute because the specified command or file was not found. Possible reasons for this include: * You misspelled a built-in dotnet command. * You intended to execute a .NET program, but dotnet-ef does not exist. * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.

```
dotnet tool install --global dotnet-ef
```

dotnet ef migrations add initial
dotnet ef database update






