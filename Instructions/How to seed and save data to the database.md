---
tags:
  - cs
  - database
  - cs-instruction
---
Sources: https://www.youtube.com/watch?v=AhAxLiGC7Pc&t=8771s
### Seeding data

(this example is for very simple operations)

```cs
protected override void OnModelCreating(ModelBuilder modelBuilder)
    {
        modelBuilder.Entity<Genre>().HasData(
            new { Id = 1, Name = "Manga" },
            new { Id = 2, Name = "Fantasy" },
            new { Id = 3, Name = "History" },
            new { Id = 4, Name = "Educational" },
            new { Id = 5, Name = "Science" }
        );

        modelBuilder.Entity<Author>().HasData(
            new { Id = 1, Name = "J.K Rolling" },
            new { Id = 2, Name = "Tsugumi Ōby" },
            new { Id = 3, Name = "Andrzej Sapkowski" },
            new { Id = 4, Name = "David McCullough" },
            new { Id = 5, Name = "Bill Bryson" }
        );
```

command to migrate seeding

```terminal
dotnet ef migrations add SeedGenres --output-dir Data\Migrations
```

AddScoped helps us to provide data for the database.
AddScoped makes sure that the dbContext is shortlift and reducing the memory over head and potentially improving performance.

### Code for saving entities to database

This example uses connect with database through BookStoreContext that is takes data from dbContext.

Its using Dtos files for data provided for CRUD.
Also Mapping is provided to simplify code structure.

Include method uses Entities to provide them to book database parameters.

Async, await it an asynchronous programming model to tell program to execute tasks at the same time.

AsNoTracking is used to send back directly to the client not to track for entity framework.

```cs
public static class BooksEndpoints
{
    const string GetBookEndpointName = "GetBook";

    public static RouteGroupBuilder MapBooksEndpoints(this WebApplication app)
    {
        var group = app.MapGroup("books")
                        .WithParameterValidation();
        // GET /books
        group.MapGet("/", async (BookStoreContext dbContext) =>
            await dbContext.Books
                     .Include(book => book.Genre)
                     .Include(book => book.Author)
                     .Select(book => book.ToBookSummaryDto())
                     .AsNoTracking()
                     .ToListAsync());
        // GET /books/1
        group.MapGet("/{id}", async (int id, BookStoreContext dbContext) =>

        {
            Book? book = await dbContext.Books.FindAsync(id);

            return book is null ? Results.NotFound() :        Results.Ok(book.ToBookDetailsDto());
        })
        .WithName(GetBookEndpointName);
       
        // POST /books
        group.MapPost("/", async (CreateBookDto newBook, BookStoreContext dbContext) =>
        {
            Book book = newBook.ToEntity();
            dbContext.Books.Add(book);
            await dbContext.SaveChangesAsync();
            return Results.CreatedAtRoute(GetBookEndpointName, new { id = book.Id }, book.ToBookDetailsDto());
        });

        // PUT /books/id
        group.MapPut("/{id}", async (int id, UpdateBookDto updatedBook, BookStoreContext dbContext) =>
        {
            var existingBook = await dbContext.Books.FindAsync(id);
            if (existingBook is null)
            {
                return Results.NotFound();
            }
            dbContext.Entry(existingBook)
                            .CurrentValues
                            .SetValues(updatedBook.ToEntity(id));
            await dbContext.SaveChangesAsync();
            return Results.NoContent();
        });
        // DELETE /book/
        group.MapDelete("/{id}", async (int id, BookStoreContext dbContext) =>
        {
            await dbContext.Books
                    .Where(book => book.Id == id)
                    .ExecuteDeleteAsync();
            return Results.NoContent();
        });
        return group;
    }
}
```

### Example for mapping

```cs
public static class BookMapping
{
    public static Book ToEntity(this CreateBookDto book)
    {
        return new Book()
        {
            Name = book.Name,
            GenreId = book.GenreId,
            Price = book.Price,
            AuthorId = book.AuthorId,
            ReleaseDate = book.ReleaseDate
        };
    }
```

[[Instructions]]
