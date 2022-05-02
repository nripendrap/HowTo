```
Install-Package NSwag.AspNet
```

```
public void ConfigureServices(IServiceCollection services) {

    ...
    ...
    ...

    services.AddOpenApiDocument(configure =>
    {
        configure.Title = "My Swagger Page";
    });
}
```

```
public void Configure(IApplicationBuilder app, IWebHostEnvironment env) {

    ...    
    ...
    ...

    app.UseOpenApi();
    app.UseSwaggerUi3();
}
```


__Hide methods from Swagger / OpenAPI documentation ASP .NET Core__
```
[ApiExplorerSettings(IgnoreApi = true)]
public class ValuesController : ControllerBase {

}
```