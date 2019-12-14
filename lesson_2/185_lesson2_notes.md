#### Assignment: Getting Started

- Revisiting the Sinatra based todo list app
- we will update the application to use a SQL database to store lists and todos
- The file is downloaded

#### Assignment: What to Focus on?

- what schema does an application require
- Project setup is secondary

#### Assignment: Project Overview

- the video went over how we will replace the interaction between application and session with interaction between DatabasePersistence class and SQL database.

#### Assignment: Extracting Session Manipulation Code

- In this video assignment, we created an ExpenseData class
- and moved all the interaction with session into that class

#### Assignment: Designing a Schema

- created a new database
- executed two `CREATE TABLE` statements to create two tables in that database `lists` and `todos`

#### Assignment: Setting up a Database Connection

- In this lesson we created a DatabasePersistence Class
- We copied and pasted the code from SessionPersistence into DatabasePersistence class
- created a connection to the database that we earlier created
- rendered the list of lists the way it was expected into our application by calling map on the PG result object.
- Now we are going to use the app interact with the database rather than the session

#### Executing and Logging Database queries

- We made use of the logger
- We defined a method called `query` in the DatabasePersistence class
- `query` method takes two arguments, sql query and params
- It then sends that query to the server returns a `PG` result object.

#### Assignment: Loading Records from the database

- Properly displayed the todos in the list and the state of those todos

#### Assignment: Solving Reloading Problem

- We can use `also_reload` sinatra method to make sure some other file reloads as well as we are developing.
- In our case, we had to provide the path to the `database_persistence.rb` file and also had to include exetension in this case.


#### Assignment: Development Configuration

- we defined another configure block in our `todo.rb` file
- and pass `:development` as an argument to that block
- and moved our reloading code in that block

#### Assignment: Working with Lists

- updated methods in the DatabasePersistence class that were dealing with lists
- adding new lists, deleting lists, updating lists

#### Assignment: Working with Todos

- updated methods in the DatabasePersistence class that were dealing with todos
- adding new todos, deleting todos, updating todos status, marking all todos as completed

#### Deploying PG Application to Heroku

- Deployed to Heroku and created a file and a gist for the steps to deploy to heroku.






















