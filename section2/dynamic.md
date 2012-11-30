# Dynamic Views

This project will demonstrate adding dynamic content using Ruby and Rails. The user will create a controller and an action in the controller.  This project also illustrates rendering content using HTML view templates using ERB, by creating a layout for the application, a view for a controller action, and a partial.


##### Generate a controller. 
```
$ rails g controller pages show
```

##### Edit routes

config/routes.rb

```ruby
Tutorial::Application.routes.draw do

  root :to => "pages#index"

end
```



##### Edit controller 

pages_controller.rb

```ruby
class Pages < ApplicationController
  
  def show
    @content = "Hello World"
    @time = Time.now
  end
  
end
```

##### Rederences

http://railscasts.com/episodes/117-semi-static-pages

