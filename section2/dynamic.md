# Dynamic Views

This project will demonstrate adding dynamic content using Ruby and Rails. The user will create a controller and an action in the controller.  This project also illustrates rendering content using HTML view templates using ERB, by creating a layout for the application, a view for a controller action, and a partial.



pages_controller.rb

```ruby

def show
  if params[:permalink]
    @page = Page.find_by_permalink(params[:permalink])
    raise ActiveRecord::RecordNotFound, "Page not found" if @page.nil?
  else
    @page = Page.find(params[:id])
  end
end


```

