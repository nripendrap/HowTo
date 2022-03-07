## Send an email using AWS Simple Email Service (SES) / AWS SDK for .NET

1. Install package __AWSSDK.SimpleEmail__

## Use AWS Parameter Store in .NET Core application
1. Install package Amazon.Extensions.Configuration.SystemsManager
.Net Configuration Extension for AWS Systems Manager

```
public static IHostBuilder CreateHostBuilder(string[] args)
{
    var config = new ConfigurationBuilder()
                    .AddJsonFile("appsettings.json", optional: false)
                    .Build();
    var awsParameterStorePath = config.GetSection("AWSParameterStorePath");

    var builder = Host.CreateDefaultBuilder(args);
    if (!string.IsNullOrEmpty(awsParameterStorePath.Value))
    {
        builder = builder.ConfigureAppConfiguration((context, builder) =>
        {
            builder.AddSystemsManager(awsParameterStorePath.Value);
        });
    }

    builder = builder.ConfigureWebHostDefaults(webBuilder =>
    {
        webBuilder.UseStartup<Startup>();
    });
    return builder;
}
```