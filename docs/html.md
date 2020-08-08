### Render HTML

*src/controllers/books/index.cr*
```crystal
class Books::Index < BaseAction
  get "/books"
  call do
    books = Book.all
    render_water "books/index"
  end
end
```

*src/views/books/index.water*
```crystal
table %|class="table table-hover"| {
  thead {
    tr {
      th "ID"
      th "Author"
      th "Name"
      th "Published At"
    } 
  }
  tbody {
    books.each do |book|
      tr {
        td book.id
        td book.author
        td book.name
        td book.published_at
      }
    end
  }
}
```

Then, output a HTML string.
```json
<table class="table table-hover">
  <thead>
    <tr>
      <th>ID</th>
      <th>Author</th>
      <th>Name</th>
      <th>Published At</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>David</td>
      <td>Crystal Programming</td>
      <td>2020-08-02 14:07:41 +08:00</td>
    </tr>
  </tbody>
</table>
```

### Render Partial

*src/views/books/index.jbuilder*
```crystal
{{ read_file("src/views/books/table.water").id }}
```

*src/views/books/table.water*
```crystal
table %|class="table table-hover"| {
  thead {
    tr {
      th "ID"
      th "Author"
      th "Name"
      th "Published At"
    } 
  }
  tbody {
    books.each do |book|
      tr {
        td book.id
        td book.author
        td book.name
        td book.published_at
      }
    end
  }
}
``` 
