# Render

### Render HTML
```crystal
class WaterExample < BaseAction
  get "/water_example"
  call do
    render_water "examples/index"
  end
end
```

### Render Plain
```crystal
class PlainExample < BaseAction
  get "/plain_example"
  call do
    render_plain "Hello World!"
  end
end
```

### Render Body
```crystal
class BodyExample < BaseAction
  get "/body_example"
  call do
    render_body "Hello World!"
  end
end
```

### Render JSON
```crystal
class JbuilderExample < BaseAction
  get "/jbuilder_example"
  call do
    render_jbuilder "examples/index"
  end
end
```
