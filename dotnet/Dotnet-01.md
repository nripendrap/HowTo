# Dotnet core MVC Page Not refreshing after changes

Add Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation NuGet package to the project
Add the following in Startup.cs:

services.AddControllersWithViews().AddRazorRuntimeCompilation();