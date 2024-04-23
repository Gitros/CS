---
tags:
  - database
  - cs
  - cs-instruction
---

Sources: https://www.youtube.com/watch?v=AhAxLiGC7Pc&t=8771s

### First step

To create a database first we need to define the classes for an app

#### Creating entity

This entity defines classes for Book and taking additional data from Genre and Author

```cs
namespace BookStore.Api.Entities;

public class Book
{
    public int Id { get; set; }
   
    public required string Name { get; set; }
   
    public int GenreId { get; set; }

    public Genre? Genre { get; set; }

    public decimal Price { get; set; }

    public int AuthorId { get; set; }

    public Author? Author { get; set; }

    public DateOnly ReleaseDate { get; set; }

}
```

```cs
namespace BookStore.Api.Entities;

public class Genre
{
    public int Id { get; set; }
   
    public required string Name { get; set; }
}
```

```cs
namespace BookStore.Api.Entities;

public class Author
{
    public int Id { get; set; }
   
    public required string Name { get; set; }
}
```

Adding proper entity framework support
NugetPackage - Microsoft.EntityFrameworkCore.Sqlite (used for this tutorial)

Create a new directory for our data related classes
(dbContext)

This code is creating a data for our database, that can be mapped to our database

Options provide details how to connet to our database

```cs
public class BookStoreContext(DbContextOptions<BookStoreContext> options)
    : DbContext(options)
```

Objects that can be mapped into our database

Db set is object that can be used to query and save instances in this case for Book Genre Author.
By doing that every object will be translated into database.

```cs
{
    public DbSet<Book> Books => Set<Book>();

    public DbSet<Genre> Genres => Set<Genre>();

    public DbSet<Author> Authors => Set<Author>();
}
```

### Connect our application to database

this code provides BookStoreContext the connect to the database

```cs
 var connString = builder.Configuration.GetConnectionString("BookStore");

builder.Services.AddSqlite<BookStoreContext>(connString);
```

json connect database

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning",
      "Microsoft.EntityFrameworkCore.Database.Command": "Warning"
    }
  },
  "AllowedHosts": "*",
  "ConnectionStrings": {
    "BookStore": "Data Source=BookStore.db"
  }
}
```

Dotnet ef is a tool that is used to do all source of entity framework tasks for application.

Microsoft.EntityFrameworkCore.Design is used to generate entity framework migrations.

Example

```terminal
dotnet ef migrations add InitialCreate --output-dir Data\Migrations
```

execute the migration

```terminal
dotnet ef database update
```

### Extension Data

A scope to interact with the database

```cs
using Microsoft.EntityFrameworkCore;

namespace BookStore.Api.Data;

public static class DataExtansions

{
    public static async Task MigrateDbAsync(this WebApplication app)
    {
      using var scope = app.Services.CreateScope();
      var dbContext = scope.ServiceProvider.GetRequiredService<BookStoreContext();
      await dbContext.Database.MigrateAsync();
    }
}
```

```cs
await app.MigrateDbAsync();
```

[[Instructions]]
