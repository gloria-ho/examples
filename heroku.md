# Additional Configurations for Heroku

## Setting Up Local Files

Configure `.yml` and create `config.ru` file
`config/database.yml`
```ruby

production:
    <<: *defaults
    url: ENV['DATABASE_URL']
```
`config.ru`
```ruby
require './app' # for app.ruby file
run Sinatra::Application
```
Run in the command line:
```
git add -A
git commit -a -m 'commit message'
```
Create a unique name for the app to live on the Heroku server:
```
heroku create UNIQUE-NAME
git push heroku master

```
Run rake db:migrate to generate tables:
```
heroku run rake db:migrate
```

## Setting Up (Private) Environment Variables
On the Heroku website, under app settings, add config vars under KEY and a long, random generated value. [Random key generator](https://randomkeygen.com/)


## Heroku Useful Commands in the Command Line

`heroku open` will open the app in your browser

To run a command:
```
heroku run #COMMAND-TO-RUN(rake db:migrate)
```

`heroku console` lets you run an environment through Heroku similar to the `irb` in your local terminal

`heroku restart` command will restart the Heroku Dynos server.

`heroku logs` and `heroku logs -t` will print logs

`heroku destroy` will delete the application


## Heroku for Rails

1. Run `heroku create `app-name

2. Run the below code:
```
heroku buildpacks:add heroku/nodejs
heroku buildpacks:add heroku/ruby
```

3. In `config/initializers/devise.rb` around line 11, uncomment and change the `config.secret_key = ENV['SECRET_KEY_BASE']`

3. In `config/environments/production.rb` around line 26, change the `config.assets.js_compressor = Uglifier.new(harmony: true)`

4. Run `heroku run rails db:migrate`