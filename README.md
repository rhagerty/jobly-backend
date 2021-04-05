
Jobly

Hello! Jobly is a Node Express REST API server for searching and connecting to jobs in a relational database. You can create/read/update/delete accounts, create/read/update/delete companies, create/read/update/delete jobs for that company, and search the database for accounts/companies/jobs. All the routes in Jobly require an auth token (provided on successful login).

Why Jobly?
This project was made during my time at Springboard, and was a great project to learn how to create RESTful APIs in Express by exercising our knowledge of database CRUDding, middleware, authentication, error handling, test writing, and JSON Schema validation.

Get Started
Download the project from this repo via Git clone or whichever method you prefer.
When in project directory:

Install dependencies by running npm install
Create PostgreSQL database named jobly and seed the database schema from data.sql by running psql jobly < data.sql
Start the server by running npm start, it should be running on localhost:3000
What Can I Do?
Here's some helpful routes to call while playing around with Jobly:

User Routes
POST localhost:3000/users
creates a new user.
data input: username, password, first_name, last_name, email, is_admin

GET localhost:3000/users
returns username, first_name, last_name and email of all users

GET localhost:3000/users/[username]
return all the fields for a user excluding the password.

PATCH localhost:3000/users/[username]
Must be the logged-in user or an admin
updates an existing user and returns the updated user excluding the password.

DELETE localhost:3000/users/[username]
Must be the logged-in user or an admin
removes an existing user and returns the message "User deleted".

Login Route
POST localhost:3000/login
authenticates user and returns an auth token.

Company Routes
GET localhost:3000/companies
This returns the handle and name for all of the company objects.
It also allows for the following query string parameters:

POST localhost:3000/companies
Must be an admin
This should create a new company and return the newly created company.
data input: handle, name, numEmployees, description, logoUrl

GET localhost:3000/companies/[handle]
This should return a single company found by its id.

PATCH localhost:3000/companies/[handle]
Must be an admin
This should update an existing company and return the updated company.

DELETE localhost:3000/companies/[handle]
Must be an admin
This should remove an existing company and return a message.

Job Routes
POST localhost:3000/jobs
Must be an admin
This route creates a new job and returns a new job.
data input: title, salary, equity, companyHandle

GET localhost:3000/jobs
This route lists all the titles and company handles for all jobs, ordered by the most recently posted jobs. It also allows for the following query string parameters:

GET localhost:3000/jobs/[id]
This route shows information about a specific job including a key of company which is an object that contains all of the information about the company associated with it.

PATCH localhost:3000/jobs/[id]
Must be an admin
This route updates a job by its ID and returns an the newly updated job.

DELETE localhost:3000/jobs/[id]
Must be an admin
This route deletes a job and returns a message.
