# Devise User Authentication


## Documentation
[Plataformatec Devise](https://github.com/plataformatec/devise)


## Setting Up

1. add `gem 'devise'` to `Gemfile`
2. run `bundle install`
3. run `rails generate devise:install`
```
rails g devise:install
      create  config/initializers/devise.rb
      create  config/locales/devise.en.yml
===============================================================================

Some setup you must do manually if you haven't yet:

  1. Ensure you have defined default url options in your environments files. Here
     is an example of default_url_options appropriate for a development environment
     in config/environments/development.rb:

       config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }

     In production, :host should be set to the actual host of your application.

  2. Ensure you have defined root_url to *something* in your config/routes.rb.
     For example:

       root to: "home#index"

  3. Ensure you have flash messages in app/views/layouts/application.html.erb.
     For example:

       <p class="notice"><%= notice %></p>
       <p class="alert"><%= alert %></p>

  4. You can copy Devise views (for customization) to your app by running:

       rails g devise:views

===============================================================================
```
4. run `rails g controller Home` to create the controller
5. create the `index.html.erb` in the `app/views/home/` folder
6. run `rails g devise User` where {User} is the name of the table
(check `/db/migrate/` to view the migrations that devise creates for you)
7. run `rails db:migrate` to create the table (run `rails routes` to check the new routes that come built-in with devise)
8. at this point, restart your server to activate the feature
9. add sign up, log in, and log out links to your views
10. to check modules, open `/app/models/` and look for the appropriate `.rb` file

If the customization at the views level is not enough, you can customize each controller by following these steps:
`rails generate devise:controllers [scope]` where scope is users
* override devise's default by adding code to `/config/routes.rb`:
```ruby
devise_for :users, controllers: {
  registrations: 'users/registrations'
}
```


## Customizing Look and Feel
* Generate all the default view files by running:
    `rails generate devise:views users`
* Style views under the `/views/` folder for each page


## Adding Columns
`rails g migration AddNameFieldsToUser first_name:string last_name:string`
`rails db:migrate`


## User Sessions
### Gets the current users information
In the controller, use the helper `current_user` to target the logged in user
### Redirect to login if user is not logged in:
In the controller, add `before_action: authenticate_user` where user is the log in
```ruby
class TodosController < ApplicationController
  before_action :authenticate_user!

  def index
    @user = current_user
    @todos = Todo.all.order(:created_at)
  end
```