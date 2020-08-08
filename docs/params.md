# Params

### Type-safe Params
An old Chinese proverb says, "If something is important, then repeat it three times". So,

**Params in Runcobo are type-safe.**

**Params in Runcobo are type-safe.**

**Params in Runcobo are type-safe.**

### Three Steps To Use Params

+ First, declare what params you expect and what type you expect by following methods: `url`, `query`, `form` and `json`.
+ Next, Runcobo parses request and wraps params to a local variable called `params`.
+ Third, use `params` variable to get or set request params.

### Url Params
```crystal
class UrlExample < BaseAction
  get "/url_example/:a/:b"
  url NamedTuple(a: Int32, b: Int32)

  call do
    sum = params[:a] + params[:b]
    render_plain sum.to_s
  end
end
```

### Query Params
```crystal
class QueryExample < BaseAction
  get "/query_example"
  query NamedTuple(a: Int32, b: Int32)

  call do
    sum = params[:a] + params[:b]
    render_plain sum.to_s
  end
end
```

### Form Params
```crystal
class FormExample < BaseAction
  post "/form_example"
  form NamedTuple(a: Int32, b: Int32)

  call do
    sum = params[:a] + params[:b]
    render_plain sum.to_s
  end
end
```

### JSON Params
```crystal
class JsonExample < BaseAction
  post "/json_example"
  json NamedTuple(a: Int32, b: Int32)

  call do
    sum = params[:a] + params[:b]
    render_plain sum.to_s
  end
end
```

### Params Merge Order
You can declare various kinds of params in a action. If params are in same key, they will be merged in following order:

`Query Params < Form Params < JSON Params < Url Params`
