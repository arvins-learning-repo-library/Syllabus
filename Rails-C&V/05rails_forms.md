# Simple Forms

https://player.vimeo.com/video/155715320

# Ruby Review

[![YouTube](http://img.youtube.com/vi/-CDpoSQTme0/0.jpg)](https://www.youtube.com/watch?v=-CDpoSQTme0)

# Rails Forms

[![YouTube](http://img.youtube.com/vi/9UGcF6pnAag/0.jpg)](https://www.youtube.com/watch?v=9UGcF6pnAag)

# Completing the User Interface

## Set Up
Let's start with a simple setup.

### Route

*config/routes.rb*

```ruby
Rails.application.routes.draw do
  post '/answers' => 'main#answers'
end
```

### Controller

*app/controllers/main_controller.rb*

```ruby
class MainController < ApplicationController

  def answers
    if params[:number].to_i.even?
      @result_string = "Even"
    else
      @result_string = "Odd"
    end
    #render "answers.html.erb"
  end

end
```

At this point the URL should work: /answers?number=43

## Using a form to enter data instead of URL

*views/main/answers.html.erb*

```erb
Number was: <%= @result_string %>
<hr/>
<form action="answers" method="post">
  <input type="text" name="number"/>
  <input type="submit" value="Submit Number"/>
</form>
```

Address bar in browser changes to: /answers?number=43
Just as if we had entered it ourselves.

## Adding Data Validation

*views/main/answers.html.erb*

```erb
Number was: <%= @result_string %>
<hr/>
<form action="answers" method="post">
  <input type="number" name="number" min="1" max="100" required/>
  <input type="submit" value="Submit Number"/>
</form>
```

## More data in a form
Adding name to form and cookies

*views/main/answers.html.erb*

```erb
<% if !@user_name.nil? %>
  Hello <%= @user_name %>!
<% end %>
Number: <%= @result_string %>
<hr/>
<form action="answers" method="post">
  <label for="number_id">Number:</label>
  <input type="number" id="number_id" name="number" min="1" max="100" required/>
  </br>
  <label for="user_name_id">Name:</label>
  <input type="text" id="user_name_id" name="user_name" />
  <br/>
  <input type="submit" value="Submit Data"/>
</form>
```

*app/controllers/main_controller.rb*

```ruby
class MainController < ApplicationController

  def answers
    if params.has_key?(:user_name) && !params[:user_name].strip.empty?
      @user_name = params[:user_name]
    else
      @user_name = "Guest"
    end

    if params[:number].to_i.even?
      @result_string = "Even"
    else
      @result_string = "Odd"
    end
    #render "answers.html.erb"
  end

end
```

# Create a Blog Post Challenge
Starting with the Blog Post Rails appliction.  Add the Ability to create new Blog Posts
- add new and create routes to the Rails Router
- add new controller endpoint
- add a form for the new action with the Blog Post form
- add create controller endpoint that process the form input 
