---
tags:
  - cs-instruction
  - cs
  - crud
  - web-api
---

Sources: https://www.youtube.com/watch?v=AhAxLiGC7Pc&t=8771s

### DTO for books

This code is for providing information that needs to be provided for CRUD

```cs
namespace BookStore.Api.Dtos;

public record class BookDto(
    int Id,
    string Name,
    string Genre,
    decimal Price,
    string Author,

    DateOnly ReleaseDate);
```

### Get all books

this code creates a path /books and displaying books that are in books method

```cs
app.MapGet("books", () => books);
```

### Get book by id

this code is for finding an id provided by the client, if the id is not existing it returns an error

```cs
app.MapGet("books/{id}", (int id) =>

{
    BookDto? book = books.Find(book => book.Id == id);
    return book is null ? Results.NotFound() : Results.Ok(book);
})

.WithName(GetGameEndpointName);
```

### Post Book

this code is used to add a new object "book" to "books" array, without providing the id becouse id depends on the books length

```cs
app.MapPost("books", (CreateBookDto newBook) =>
{
    BookDto book = new(
        books.Count + 1,
        newBook.Name,
        newBook.Genre,
        newBook.Price,
        newBook.Author,
        newBook.ReleaseDate);
       
    books.Add(book);
    return Results.CreatedAtRoute(GetGameEndpointName, new { id = book.Id }, book);
});
```

### Put book

this code is used to update values for an object with id specified by a client.

```cs
app.MapPut("books/{id}", (int id, UpdateBookDto updatedBook) =>
{

    var index = books.FindIndex(book => book.Id == id);
    if (index == -1)
    {
        return Results.NotFound();
    }
    books[index] = new BookDto(
        id,
        updatedBook.Name,
        updatedBook.Genre,
        updatedBook.Price,
        updatedBook.Author,
        updatedBook.ReleaseDate
    );
    return Results.NoContent();
});
```

### Delete book

this code is used to delete an object from books specified by a client.

```cs
app.MapDelete("books/{id}", (int id) =>
{
    books.RemoveAll(book => book.Id == id);
    return Results.NoContent();
});
```

### Http code

code for client to send request to the server

```http
GET http://localhost:5070/books

###

GET http://localhost:5070/books/4

###

POST http://localhost:5070/books
Content-Type: application/json

{
    "name": "Tokyo ghoul",
    "genre": "Manga",
    "price": "20.99",
    "author": "Sui Ishida",
    "releaseDate": "2011-10-21"
}
###
PUT http://localhost:5070/books/5
Content-Type: application/json
{
    "name": "Harry Potter 2",
    "genre": "Fantasy",
    "price": 25.51,
    "author": "J.K Rolling",
    "releaseDate": "2020-09-12"
}
###
DELETE http://localhost:5070/books/1
```
