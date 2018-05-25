# ActiveRecord

Classes respond to => Table

Instances respond to => Row / Records

## Define a Table
* plural name
* lower case / snake case

## Define a Model Class
* singluar version of the pluralized table name
* capitalized / camel case
* inherit from `ActiveRecord::Base`

## Creating a New Instance of a Class
* `Class.create()` - saves to database automatically
* `variable = Class.new()` - does not save until you call the save method
* `variable.save` - save method to save the instance

## Search for Data
### Return a single record
* `Class.find(some_id)`
* `Class.find_by(search_by_attribute/column_names)`

### Return an array with multiple records
* `Class.where(search_by_attribute/column_names)`

## Updating 
* `instance.update(`...`)` - updated in the database
* `instance.attribute =` ... - will update the instance but does not save until you call the save method
* `instance.save` - save method to save the instance

## Deleting
* `instance.destroy` - deletes the instance
* `Table.destroy(id_number)` - destorys record by ID number
* `Table.destroyall` - destroys every record in the table

## Relationships

### One-to-One
ClassA's id is being referenced in ClassB, therefor ClassB `belongs_to :class_a` (creates a `:class_a` method on the instance)

ClassA `has_one :classB` (creates a `class_b` method on the instance)

### One-to-Many
ClassA `has_many :class_bs` *(plural)*
ClassB `belongs_to :class_a`

Creates methods that can be called:
```sql
a = ClassA.find(...)
a.class_bs
b = ClassB.find(...)
b.class_a
```

### Many-to-Many
With three tables, Person, Car, and PersonCar:
Person `has_many :person_cars`
Person `has_many :cars, through: :person_cars` (must specify the join table)
Car `has_many :person_cars`
Car `has_many :persons, through: person_cars` (must specify the join table)
PersonCar `belongs_to :person`
PersonCar `belongs_to :car`

Creates methods that can be called:
```sql
my_person = Person.find(..)
my_person.cars
my_person.cars << card.find(..)
car.create(property1: 'value1', property2: 'value2')
```

# Rakefile
`rake db:create_migration NAME=`name_of_change

## Step 1
Create the db
`rake db:create_migration`
## Step 2
Define the what the migration is
```
def change
  create_table :todo |t|
    t.string :name
    t.string :description
  end
end
```
## Step 3
Migrate
`rake db:migrate`

