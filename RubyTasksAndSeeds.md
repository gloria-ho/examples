# Custom Rake Tasks

## (like db:create, db:migrate, etc.) For generating dummy data

In the `/lib/tasks/` folder, create a new file with an extension of `.rake` (example: create_dummy_data.rake) and write the command code.

Example:
```ruby
namespace :dummy do 
  task create_todos: :environment do
    10.times do |i|
      Todo.create(
        name: i.to_s * 4,
        description: "Dummy description: #{i}",
        priority: 'H'
        )
    end
  end

```


In terminal, run `rake {namespace_name}:{task_name}`

## Hints:

* You don't need the namespace, but it is common practice

* To destroy all data you can go into terminal and run `Table.detroy_all`

* Gem: Faker for generating dummy data

# Rails Seeds

## For generating a set number of data

In the `db/seeds.rb` file, write the seed code.

Example:
```ruby
priorities = [{
  name: 'High Priority',
  code: 'H'
}, {
  name: 'Medium Priority',
  code: 'M'
}, {
  name: 'Low Priority',
  code: 'L'
}]

priorities.each do |p| 
```


Run `rails db:seed`

# To run all database commands at once

If you drop all the databases with `rails db:drop`, you can run one command to re-create new data.

`rails db:setup` will run :create, :migrate, and :seed together.