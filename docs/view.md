# View

Runcobo renders JSON by **Jbuilder**, renders HTML by **Water**.
**Jbuilder** is a template engine designed for json using plain Crystal.
**Water** is a template engine designed for html using plain Crystal.

### Data transfer
All methods or variables defined in the action are available in the views.
This is because the views are compiled in the same scope as the action.

### Layout

You can override the default layout conventions in your actions by using the layout declaration. For example:
```crystal
class BaseAction
  layout "application"
  #...
end
```

### Partial

Runcobo renders partial view by build-in `read_file` macro. There's no magic about partial view. 
For example,

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