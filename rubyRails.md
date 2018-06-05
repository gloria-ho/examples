# Rails


## Create a New App

`rails new` [options]

`rails new rails_todos --skip-coffee --skip-action-cable --skip-active-storage --skip-turbolinks --database=postgresql`

**To start a new server environment:**

`rails start` or `rails s`

**To start database**

`rails db:create`


## Generate Models

**To generate**

`rails generate` model_name col_name`:`model_type

or

`rails g` model_name col_name`:`model_type

*Example:*
`rails g model Todo name:string description:string`


## Programming Design Pattern: MVC *(Model View Controller)*

**Model:** Interacts with database

**View:** All the erb's, Determine how the pages will be rendered on the screen.

**Controllers:**
* Process/recieve requests and issue a response
* Need to work with the models to update/read the database.
* Need to work with the views to render our pages.


## Resources

*Resources* correspond to tables in our database.

* Each resource needs a model and a controller.
  * Each controller needs a subdirectory inside the `views` folder (where subdrectory name matches the controller name).
    * Each `.erb` file coresponds to the methods/actions on the controller (where `.erb` file name matches the method name).


## Rails Console

`rails console` or `rails c`

Rails will automatically require.


## Routes

Create a route with the page and direct to the controller.


## Controller

* Every controller needs a sub-directory inside the `views` folder (matching the name of the controller).


`rails g controller --help`

```ruby
Rails.application.routes.draw do
  # For details on the DSL available within this file, see http://guides.rubyonrails.org/routing.html

  get '/todos', to: 'todos#index'
  get '/todos/new', to: 'todos#new'
  post '/todos/create', to: 'todos#create'
  get '/todos/edit:id', to: 'todos#edit'
  put '/todos/edit/:id', to: 'todos#update'
  delete '/todos/:id', to: 'todos#destroy'

end
```
Results:
```
      Prefix Verb   URI Pattern               Controller#Action
       todos GET    /todos(.:format)          todos#index
   todos_new GET    /todos/new(.:format)      todos#new
todos_create POST   /todos/create(.:format)   todos#create
             GET    /todos/edit:id(.:format)  todos#edit
             PUT    /todos/edit/:id(.:format) todos#update
             DELETE /todos/:id(.:format)      todos#destroy
```

```ruby
Rails.application.routes.draw do

  resources :todos

end
```

Results:
```
   Prefix Verb   URI Pattern               Controller#Action
    todos GET    /todos(.:format)          todos#index
          POST   /todos(.:format)          todos#create
 new_todo GET    /todos/new(.:format)      todos#new
edit_todo GET    /todos/:id/edit(.:format) todos#edit
     todo GET    /todos/:id(.:format)      todos#show
          PATCH  /todos/:id(.:format)      todos#update
          PUT    /todos/:id(.:format)      todos#update
          DELETE /todos/:id(.:format)      todos#destroy
```


## Display routes

`rails routes`

**View Helpers**

*There are built in helpers in rails. You can define your own helpers under the `/helpers/` directory.*

Only availables in `views` and `controllers`:
* `_path` - gives the path
* `_url` - gives the entire domain


## Form Helper

`form_for` @instance_name `do |f|`
html
`end`

```
<%= form_for do |f| %>
  <div>
    <%= f.label :name %>
    <%= f.text_field :name %>
  </div>

  <div>
    <%= f.label :description %>
    <%= f.text_field :descriptio %>
  </div>

  <div>
    <%= f.submit %>
  </div>
<% end %>
```


## Taking in Parameters

table_name`.create(toto_params)`

**Private parameters**
```
  def table_params
    params.require(:todo).permit(:name, :description)
  end
```


## Rendering .erb

When repeating code, you can save the code under the views folder as `_`name`.html.erb`

To render the code, use `<%= render `name` %>` on the .erb page.


## Delete

`<a href="<%= table_path(variable) %>" data-method="DELETE">`


## Unobtrusive JavaScript

`data-method="DELETE"`

`data-disable-with="Processing..."`


## Steps

`rails new app_name [options]`

`rails db:create`

`rails start` or `rails s`
  * start the local server

`rails generate model myModel col:type col:type` or `rails g model myModel col:type col:type`
  * create your migration file `/db/` and model class `/app/models/`

`rails db:migrate`
  * update your databse with the migration

`rails console`

`rails generate controller ResourceController/Table_plural` or `rails g controller ResourceController/Table_plural`
  * create a controller class `/app/controllers/`

create routes
  * update `/config/routes.rb`
    * `resourses :todos`
      or
    * create `index.html.erb` inside `/views/table/` using the method name.

check routes: `rails routes`
  * define the methods on the controller that correspond to the routes created

create the `.erb`'s that coresspond to the `GET` methods

write the code


## Scaffold

`rails g scaffold Post name:string content:text catagory:string`


## Help

Run `rails new --help`

```
Usage:
  rails new APP_PATH [options]

Options:
      [--skip-namespace], [--no-skip-namespace]            # Skip namespace (affects only isolated applications)
  -r, [--ruby=PATH]                                        # Path to the Ruby binary of your choice
                                                           # Default: /usr/local/Cellar/ruby/2.5.1/bin/ruby
  -m, [--template=TEMPLATE]                                # Path to some application template (can be a filesystem path or URL)
  -d, [--database=DATABASE]                                # Preconfigure for selected database (options: mysql/postgresql/sqlite3/oracle/frontbase/ibm_db/sqlserver/jdbcmysql/jdbcsqlite3/jdbcpostgresql/jdbc)
                                                           # Default: sqlite3
      [--skip-yarn], [--no-skip-yarn]                      # Don't use Yarn for managing JavaScript dependencies
      [--skip-gemfile], [--no-skip-gemfile]                # Don't create a Gemfile
  -G, [--skip-git], [--no-skip-git]                        # Skip .gitignore file
      [--skip-keeps], [--no-skip-keeps]                    # Skip source control .keep files
  -M, [--skip-action-mailer], [--no-skip-action-mailer]    # Skip Action Mailer files
  -O, [--skip-active-record], [--no-skip-active-record]    # Skip Active Record files
      [--skip-active-storage], [--no-skip-active-storage]  # Skip Active Storage files
  -P, [--skip-puma], [--no-skip-puma]                      # Skip Puma related files
  -C, [--skip-action-cable], [--no-skip-action-cable]      # Skip Action Cable files
  -S, [--skip-sprockets], [--no-skip-sprockets]            # Skip Sprockets files
      [--skip-spring], [--no-skip-spring]                  # Don't install Spring application preloader
      [--skip-listen], [--no-skip-listen]                  # Don't generate configuration that depends on the listen gem
      [--skip-coffee], [--no-skip-coffee]                  # Don't use CoffeeScript
  -J, [--skip-javascript], [--no-skip-javascript]          # Skip JavaScript files
      [--skip-turbolinks], [--no-skip-turbolinks]          # Skip turbolinks gem
  -T, [--skip-test], [--no-skip-test]                      # Skip test files
      [--skip-system-test], [--no-skip-system-test]        # Skip system test files
      [--skip-bootsnap], [--no-skip-bootsnap]              # Skip bootsnap gem
      [--dev], [--no-dev]                                  # Setup the application with Gemfile pointing to your Rails checkout
      [--edge], [--no-edge]                                # Setup the application with Gemfile pointing to Rails repository
      [--rc=RC]                                            # Path to file containing extra configuration options for rails command
      [--no-rc], [--no-no-rc]                              # Skip loading of extra configuration options from .railsrc file
      [--api], [--no-api]                                  # Preconfigure smaller stack for API only apps
  -B, [--skip-bundle], [--no-skip-bundle]                  # Don't run bundle install
      [--webpack=WEBPACK]                                  # Preconfigure for app-like JavaScript with Webpack (options: react/vue/angular/elm/stimulus)

Runtime options:
  -f, [--force]                    # Overwrite files that already exist
  -p, [--pretend], [--no-pretend]  # Run but do not make any changes
  -q, [--quiet], [--no-quiet]      # Suppress status output
  -s, [--skip], [--no-skip]        # Skip files that already exist

Rails options:
  -h, [--help], [--no-help]        # Show this help message and quit
  -v, [--version], [--no-version]  # Show Rails version number and quit

Description:
    The 'rails new' command creates a new Rails application with a default
    directory structure and configuration at the path you specify.

    You can specify extra command-line arguments to be used every time
    'rails new' runs in the .railsrc configuration file in your home directory.

    Note that the arguments specified in the .railsrc file don't affect the
    defaults values shown above in this help message.

Example:
    rails new ~/Code/Ruby/weblog

    This generates a skeletal Rails installation in ~/Code/Ruby/weblog.
```


`rails g model --help`

```
Usage:
  rails generate model NAME [field[:type][:index] field[:type][:index]] [options]

Options:
      [--skip-namespace], [--no-skip-namespace]  # Skip namespace (affects only isolated applications)
      [--force-plural], [--no-force-plural]      # Forces the use of the given model name
  -o, --orm=NAME                                 # ORM to be invoked
                                                 # Default: active_record

ActiveRecord options:
      [--migration], [--no-migration]        # Indicates when to generate migration
                                             # Default: true
      [--timestamps], [--no-timestamps]      # Indicates when to generate timestamps
                                             # Default: true
      [--parent=PARENT]                      # The parent class for the generated model
      [--indexes], [--no-indexes]            # Add indexes for references and belongs_to columns
                                             # Default: true
      [--primary-key-type=PRIMARY_KEY_TYPE]  # The type for primary key
  -t, [--test-framework=NAME]                # Test framework to be invoked
                                             # Default: test_unit

TestUnit options:
      [--fixture], [--no-fixture]   # Indicates when to generate fixture
                                    # Default: true
  -r, [--fixture-replacement=NAME]  # Fixture replacement to be invoked

Runtime options:
  -f, [--force]                    # Overwrite files that already exist
  -p, [--pretend], [--no-pretend]  # Run but do not make any changes
  -q, [--quiet], [--no-quiet]      # Suppress status output
  -s, [--skip], [--no-skip]        # Skip files that already exist

Description:
    Stubs out a new model. Pass the model name, either CamelCased or
    under_scored, and an optional list of attribute pairs as arguments.

    Attribute pairs are field:type arguments specifying the
    model's attributes. Timestamps are added by default, so you don't have to
    specify them by hand as 'created_at:datetime updated_at:datetime'.

    As a special case, specifying 'password:digest' will generate a
    password_digest field of string type, and configure your generated model and
    tests for use with Active Model has_secure_password (assuming the default ORM
    and test framework are being used).

    You don't have to think up every attribute up front, but it helps to
    sketch out a few so you can start working with the model immediately.

    This generator invokes your configured ORM and test framework, which
    defaults to Active Record and TestUnit.

    Finally, if --parent option is given, it's used as superclass of the
    created model. This allows you create Single Table Inheritance models.

    If you pass a namespaced model name (e.g. admin/account or Admin::Account)
    then the generator will create a module with a table_name_prefix method
    to prefix the model's table name with the module name (e.g. admin_accounts)

Available field types:

    Just after the field name you can specify a type like text or boolean.
    It will generate the column with the associated SQL type. For instance:

        `rails generate model post title:string body:text`

    will generate a title column with a varchar type and a body column with a text
    type. If no type is specified the string type will be used by default.
    You can use the following types:

        integer
        primary_key
        decimal
        float
        boolean
        binary
        string
        text
        date
        time
        datetime

    You can also consider `references` as a kind of type. For instance, if you run:

        `rails generate model photo title:string album:references`

    It will generate an `album_id` column. You should generate these kinds of fields when
    you will use a `belongs_to` association, for instance. `references` also supports
    polymorphism, you can enable polymorphism like this:

        `rails generate model product supplier:references{polymorphic}`

    For integer, string, text and binary fields, an integer in curly braces will
    be set as the limit:

        `rails generate model user pseudo:string{30}`

    For decimal, two integers separated by a comma in curly braces will be used
    for precision and scale:

        `rails generate model product 'price:decimal{10,2}'`

    You can add a `:uniq` or `:index` suffix for unique or standard indexes
    respectively:

        `rails generate model user pseudo:string:uniq`
        `rails generate model user pseudo:string:index`

    You can combine any single curly brace option with the index options:

        `rails generate model user username:string{30}:uniq`
        `rails generate model product supplier:references{polymorphic}:index`

    If you require a `password_digest` string column for use with
    has_secure_password, you can specify `password:digest`:

        `rails generate model user password:digest`

    If you require a `token` string column for use with
    has_secure_token, you can specify `auth_token:token`:

        `rails generate model user auth_token:token`

Examples:
    `rails generate model account`

        For Active Record and TestUnit it creates:

            Model:      app/models/account.rb
            Test:       test/models/account_test.rb
            Fixtures:   test/fixtures/accounts.yml
            Migration:  db/migrate/XXX_create_accounts.rb

    `rails generate model post title:string body:text published:boolean`

        Creates a Post model with a string title, text body, and published flag.

    `rails generate model admin/account`

        For Active Record and TestUnit it creates:

            Module:     app/models/admin.rb
            Model:      app/models/admin/account.rb
            Test:       test/models/admin/account_test.rb
            Fixtures:   test/fixtures/admin/accounts.yml
            Migration:  db/migrate/XXX_create_admin_accounts.rb
```

`rails g controller --help`
```
Usage:
  rails generate controller NAME [action action] [options]

Options:
      [--skip-namespace], [--no-skip-namespace]  # Skip namespace (affects only isolated applications)
      [--skip-routes], [--no-skip-routes]        # Don't add routes to config/routes.rb.
      [--helper], [--no-helper]                  # Indicates when to generate helper
                                                 # Default: true
      [--assets], [--no-assets]                  # Indicates when to generate assets
                                                 # Default: true
  -e, [--template-engine=NAME]                   # Template engine to be invoked
                                                 # Default: erb
  -t, [--test-framework=NAME]                    # Test framework to be invoked
                                                 # Default: test_unit

Asset options:
  -j, [--javascripts], [--no-javascripts]       # Generate JavaScripts
                                                # Default: true
  -y, [--stylesheets], [--no-stylesheets]       # Generate Stylesheets
                                                # Default: true
  -je, [--javascript-engine=JAVASCRIPT_ENGINE]  # Engine for JavaScripts
                                                # Default: js
  -se, [--stylesheet-engine=STYLESHEET_ENGINE]  # Engine for Stylesheets
                                                # Default: scss

Runtime options:
  -f, [--force]                    # Overwrite files that already exist
  -p, [--pretend], [--no-pretend]  # Run but do not make any changes
  -q, [--quiet], [--no-quiet]      # Suppress status output
  -s, [--skip], [--no-skip]        # Skip files that already exist

Description:
    Stubs out a new controller and its views. Pass the controller name, either
    CamelCased or under_scored, and a list of views as arguments.

    To create a controller within a module, specify the controller name as a
    path like 'parent_module/controller_name'.

    This generates a controller class in app/controllers and invokes helper,
    template engine, assets, and test framework generators.

Example:
    `rails generate controller CreditCards open debit credit close`

    CreditCards controller with URLs like /credit_cards/debit.
        Controller: app/controllers/credit_cards_controller.rb
        Test:       test/controllers/credit_cards_controller_test.rb
        Views:      app/views/credit_cards/debit.html.erb [...]
        Helper:     app/helpers/credit_cards_helper.rb
```

`rails routes`
```
Usage:
  rails new APP_PATH [options]

Options:
      [--skip-namespace], [--no-skip-namespace]            # Skip namespace (affects only isolated applications)
  -r, [--ruby=PATH]                                        # Path to the Ruby binary of your choice
                                                           # Default: /usr/local/Cellar/ruby/2.5.1/bin/ruby
  -m, [--template=TEMPLATE]                                # Path to some application template (can be a filesystem path or URL)
  -d, [--database=DATABASE]                                # Preconfigure for selected database (options: mysql/postgresql/sqlite3/oracle/frontbase/ibm_db/sqlserver/jdbcmysql/jdbcsqlite3/jdbcpostgresql/jdbc)
                                                           # Default: sqlite3
      [--skip-yarn], [--no-skip-yarn]                      # Don't use Yarn for managing JavaScript dependencies
      [--skip-gemfile], [--no-skip-gemfile]                # Don't create a Gemfile
  -G, [--skip-git], [--no-skip-git]                        # Skip .gitignore file
      [--skip-keeps], [--no-skip-keeps]                    # Skip source control .keep files
  -M, [--skip-action-mailer], [--no-skip-action-mailer]    # Skip Action Mailer files
  -O, [--skip-active-record], [--no-skip-active-record]    # Skip Active Record files
      [--skip-active-storage], [--no-skip-active-storage]  # Skip Active Storage files
  -P, [--skip-puma], [--no-skip-puma]                      # Skip Puma related files
  -C, [--skip-action-cable], [--no-skip-action-cable]      # Skip Action Cable files
  -S, [--skip-sprockets], [--no-skip-sprockets]            # Skip Sprockets files
      [--skip-spring], [--no-skip-spring]                  # Don't install Spring application preloader
      [--skip-listen], [--no-skip-listen]                  # Don't generate configuration that depends on the listen gem
      [--skip-coffee], [--no-skip-coffee]                  # Don't use CoffeeScript
  -J, [--skip-javascript], [--no-skip-javascript]          # Skip JavaScript files
      [--skip-turbolinks], [--no-skip-turbolinks]          # Skip turbolinks gem
  -T, [--skip-test], [--no-skip-test]                      # Skip test files
      [--skip-system-test], [--no-skip-system-test]        # Skip system test files
      [--skip-bootsnap], [--no-skip-bootsnap]              # Skip bootsnap gem
      [--dev], [--no-dev]                                  # Setup the application with Gemfile pointing to your Rails checkout
      [--edge], [--no-edge]                                # Setup the application with Gemfile pointing to Rails repository
      [--rc=RC]                                            # Path to file containing extra configuration options for rails command
      [--no-rc], [--no-no-rc]                              # Skip loading of extra configuration options from .railsrc file
      [--api], [--no-api]                                  # Preconfigure smaller stack for API only apps
  -B, [--skip-bundle], [--no-skip-bundle]                  # Don't run bundle install
      [--webpack=WEBPACK]                                  # Preconfigure for app-like JavaScript with Webpack (options: react/vue/angular/elm/stimulus)

Runtime options:
  -f, [--force]                    # Overwrite files that already exist
  -p, [--pretend], [--no-pretend]  # Run but do not make any changes
  -q, [--quiet], [--no-quiet]      # Suppress status output
  -s, [--skip], [--no-skip]        # Skip files that already exist

Rails options:
  -h, [--help], [--no-help]        # Show this help message and quit
  -v, [--version], [--no-version]  # Show Rails version number and quit

Description:
    The 'rails new' command creates a new Rails application with a default
    directory structure and configuration at the path you specify.

    You can specify extra command-line arguments to be used every time
    'rails new' runs in the .railsrc configuration file in your home directory.

    Note that the arguments specified in the .railsrc file don't affect the
    defaults values shown above in this help message.

Example:
    rails new ~/Code/Ruby/weblog

    This generates a skeletal Rails installation in ~/Code/Ruby/weblog.
```