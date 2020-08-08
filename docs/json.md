### Render JSON

*src/controllers/books/index.cr*
```crystal
class Books::Index < BaseAction
  get "/books"
  call do
    books = Book.all
    render_jbuilder "books/index"
  end
end
```

*src/views/books/index.jbuilder*
```crystal
json.array! "books", books do |json, book|
  json.book_id      book.id
  json.author       book.author
  json.name         book.name
  json.published_at book.published_at
end
```

Then, output a JSON string.
```json
{
  "books": [{
    "book_id": 1,
    "author": "David",
    "name": "Crystal Programming",
    "published_at": "2020-08-08T20:00:00+00:00"
  }]
}
```

### Render Partial

*src/views/books/index.jbuilder*
```crystal
json.array! "books", books do |json, book|
  {{ read_file("src/views/books/_base_book.jbuilder").id }}
end
```

*src/views/books/_base_book.jbuilder*
```crystal
json.book_id      book.id
json.author       book.author
json.name         book.name
json.published_at book.published_at
```