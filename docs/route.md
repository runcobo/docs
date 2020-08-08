# Route
Runcobo declares routes in every Actions. If you access the route, it will run into related Action.

In this way, you can know the routes of current Action quickly.

You can declare RESTful routes as you want or not.

> In my personal view, RESTful is too abstact when you were far way from a CRUD system like Backend Management System.

> When writing API, I believe urls should be named like functions, not objects or resources.

> When writing a Backend Management System, enjoy RESTful.

### Routes Declaration
Runcobo declares routes by following methods: `get`, `post`, `put`, `patch`, `delete`, `options`, `head`.
An Action can bind to one or more routes.

```crystal
class Example < BaseAction
  get "/books"
  get "/books/:id"
  post "/books"
  put "/books/:id"
  patch "/books/:id"
  delete "/books/:id"
  options "/books/:id"
  head "/books/:id"

  call do
    render_plain "Hello World"
  end
end
```

### URL Params
URL Params can be declared in the route like `/add/:apple_count/:banana_count`. And then you should use `url` method to declare the type of URL params.

```crystal
class Example < BaseAction
  get "/add/:apple_count/:banana_count"
  url NamedTuple(apple_count: Int32, banana_count: Int32)

  call do
    sum = params[:apple_count] + params[:banana_count]
    render_plain sum.to_s
  end
end
```

### Custom HTTP method
If you need a route with custom HTTP method, such as `LINK`, `UNLINK`, `FIND` or `PURGE`, then you can use `route` method to declare it.

```crystal
class Example < BaseAction
  route "LINK", "/books/:id"

  call do
    render_plain "Hello World"
  end
end
```
