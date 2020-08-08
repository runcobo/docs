# Getting Started

1.Init a Crystal project.
```shell
crystal init app demo && cd demo
```

2.Add the dependency to your shard.yml and run `shards install`.
```yaml
dependencies:
  runcobo:
    github: runcobo/runcobo
```

3.Write down the following code in `src/demo.cr`.
```crystal
require "runcobo"

class Api::V1::Add < BaseAction
  get "/api/v1/add"
  query NamedTuple(a: Int32, b: Int32)

  call do
    sum = params[:a] + params[:b]
    render_plain sum.to_s
  end
end

Runcobo.start
```

4.Run server.
```shell
crystal src/demo.cr
```

5.Send request.
```shell
curl "http://0.0.0.0:3000/api/v1/add?a=1&b=2"
```