<!-- Notes from Lesson 1 of course 185 -->

#### Assignment: What this course covers?

- Learn how to interact with a database using a programming language (Ruby).
- In particular we will learn how to use `pg` gem to work with a postgreSQL database
- How to apply your knowledge of `ruby` and `sql` together

#### Assignment: Getting Started

- We will use the `pg` library
- connect to `postgreSQL` with `ruby`
- use the `pg` gem to perform queries
- build dynamic `SQL` statements safely
- structure small command-line applications
- optimize queries made from `ruby` programs

#### Assignment: What to Focus on

- Observe the progression of steps from high-level requirements to low-level implementation details
- Think about how project requirements affect what SQL is written
- Understand how to dynamically generate SQL
- Focus on database and not the application

#### Assignment: Execcuting SQL statements from Ruby

- Create a connection to the databae:
  - `PG.connect(dbname: "films")` => will return a connectoin object through which we could talk to the database
- Send an SQL statement to the database:
  - `db.exec("SELECT 1")` => by calling the exec method on the database connection object `db`. This will result a `PG` result object.
- Using `PG` result object to see what we get back from the server
  - `result.values` => will return array of arrays

**So What we did in this lesson**

```ruby
db = PG.connect # created a database connection
result = db.exec("SELECT * FROM films") # sent an SQL query to the server

# Then we call several methods on the result object that is returned by the method call `exec`

# For example

result.values
result.fields
result.ntuples
result.each(&block)
result.each_row(&block)
result[index]
result.field_values(column_name)
result.column_values(index)

```
#### Assignment: Project Demo

The video in the lesson just gave us demo of the project that we will be building. It's an expense recorder command-line application

#### Assignment: Project Setup

- We created a directory for our project
- Created new `Gemfile` and added `pg` gem
- created new file called `expense`
- added `hash-bang` to the top of the file `#! /usr/bin/env ruby` which allows shell program to execute the script using ruby
- Added execute permission to the file `expense` with the terminal command `chmod +x expense`
- require the `pg` gem within expense file

#### Assignment: Database Design

- Designed Database that we are going to use
- created database called `expenses`
- executed the following SQL statement

```SQL
CREATE TABLE expenses (
  id serial PRIMARY KEY,
  amount numeric(6,2) NOT NULL,
  memo text NOT NULL,
  created_at date NOT NULL
);

ALTER TABLE expenses
  ADD CHECK (amount > 0);
```
#### Assignment: Listing Expenses

- in this lesson we created a connection with the database and executed the following code to display all expenses
```ruby

db = PG.connect(dbname: "expenses")

result = db.exec("SELECT * FROM expenses")

result.each do |tuple|
  columns = [ tuple["id"].rjust(3),
              tuple["created_on"].rjust(10),
              tuple["amount"].rjust(12),
              tuple["memo"] ]
  puts columns.join(" | ")
end

```

#### Assignment: Displaying Help

- We used the constant `ARGV` to decide what arguments were passed into the command `./expense`
- based on those arguments, we either display info or list all expenses

#### Assignment: Adding Expenses

- In this assignment, we defined another method to add expenses to the list
- If the first argument is `add` then there should also be an amount and memo
- If amount or memo is missing we throw a message and exit out of the program

#### Assignment: Handling Parameter Safely

- We learned how it is very important to make sure that some malicious input to the server won't affect us badly
- We learned to use PG result object method `exec_params` instead of `exec`

#### Assignment: Code Structure

- In this assignment we separated the code responsibility
- We created a `ExpenseData` class and a `CLI` class
- And moved the `add` and `list` methods into the expense data class
- While we moved the parameter handling code into `CLI` class

#### Assignment: Search Expenses

- We defined another method in `ExpenseData` class called `search`
- `search` method takes one argument and searches the database and returns if there are any matching results
- We used the same code for displaying purposes as in the `list` method


















