## Entity Framework Code First 101

#### Run EF command from Package Manager Console.

###### Where is Package Manager Console in Visual Studio?
Tools -> NuGet Package Manager -> Package Manager Console

###### View EF Commands
```
Get-Help EntityFramework
```

###### Getting Help
```
Get-Help Update-Database
```

###### Creating a new model
1. Add a User class to the model
Example:
```
public class User
{
    public string Username { get; set; }
    public string DisplayName { get; set; }
}
```
2. Add a set to the context
Example:
```
public class BloggingContext : DbContext
{
    public DbSet<Blog> Blogs { get; set; }
    public DbSet<Post> Posts { get; set; }
    public DbSet<User> Users { get; set; }
}
```
3. Type these commands in the package manager console
```
Add-Migration AddUser -Context BloggingContext
Update-Database -Context BloggingContext
```

###### Adding new properties to the existing model/Changing model
1.  Add new property to the the model class
Example
```
public class User
{
    public string Username { get; set; }
    public string DisplayName { get; set; }
    public int Age { get; set; } <== new property
}
```
2. Then run these commands in package manager console
```
Add-Migration AddColumnAgeTableUser -Context BloggingContext
Update-Database -Context BloggingContext
```

###### Rollback
1. Run this command
```
Update-Database -Migration <Last script to keep> -Context <Database context>

Example:
Update-Database -Migration 20180911024005_AddColumnFirstNameInUser -Context BloggingContext
```
2. Then modify the code