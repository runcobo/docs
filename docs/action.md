# Action

Runcobo use one action one file. 

### Before Filter
```crystal
class BeforeExample < BaseAction
  before required_login
  def required_login
    Runcobo::Log.info { "Required Login" }
  end

  get "/before_example"
  call do
    render_plain "Hello World!"
  end
end
```

### After Filter
```crystal
class BeforeExample < BaseAction
  after log_params
  def log_params
    Runcobo::Log.info { "#{params}" }
  end

  get "/before_example"
  call do
    render_plain "Hello World!"
  end
end
```

### Skip Filter
```crystal
class BaseAction
  before required_login
  def required_login
    Runcobo::Log.info { "Required Login" }
  end
end

class SkipExample < BaseAction
  skip required_login

  get "/before_example"
  call do
    render_plain "Hello World!"
  end
end
```
