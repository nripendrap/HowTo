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