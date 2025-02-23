# CoderManagement

CoderManagement is a platform that helps individuals and teams manage their tasks.
These are more than just simple to-do lists. Task management tools allow teams to collaborate digitally by organizing, prioritizing, and assigning tasks to each other.

So what exactly does task management software do?


# Overview
You're the CEO of a small tech start-up company.
After a while, you realize that you need a system that can keep track of the tasks and improve productivity.
As this is just an internal mini-project of the company, your goal is also to keep the cost low.
Remembering your amazing time at CoderSchool learning how to code, you roll up your sleeves and start up your Visual Studio Code.

As a wise programmer, you started off planning for an MVP (Minimum Viable Product). For the first phase of this product:

Entity relationship diagram
You came up with this design.

# ERD

Features
You have decided for this first phase of the application that:

You are the only manager who assigns task
Your team members are an employee
Your team members could sign up for an account with their name and become employees by default
You will create, assign and delete tasks to other users
A user may have one, many, or no task he/she is responsible for.
A task may have one or no one asign to it yet
Right now, you are the only user of this project, so no authentication is needed

Description
Everyone who uses the app is a user. There are 2 roles for user: employee and manager
You are the user that has higher authority in the company ( later could be other managers).
This hierarchy of roles allows us to limit access to certain features in the application that only the manager has permission.

However, at this stage, you just want to warm up your coding skills and make the most straightforward version as fast as possible.

End points requirements
For now, your account will be created through Compass with the role: manager

Design your routes so that from a client app, you can:

User
Create a new user with user's name. The default role is employee.
Get all users with filters. You can decide yourself which queries you allow in the request based on the User schema.
Search for an employee by name
Get all tasks of 1 user (Decide which one is better: by name or by id?)
Task
Create a task with the required information.
Browse your tasks with filter allowance (name, status, createdAt,…). The following attributes are required to help filtering tasks by status, and help sorting by createdAt, updatedAt
status
createdAt,updatedAt
Get a single task by id.

Assign a task to a user or unassign them

Update the status of a task.
There's a rule for updating task status: when the status is set to done, it can't be changed to other value except archive

Soft delete a task. Remember how you did this in previous assignments?

Research and Apply: In backend development, input validation is an important step. This time, you are required to research on express-validator and apply further API request input control:

Create user request must check body for : existence, including name , name's value is a valid string.
Create task request must check body for : existence, and other requirements per task schema.
All routes that require _id , must be checked for its existence and whether it is a mongo object id.

Schema hint
In the real world, schema design is often the responsibility of senior devs. However, it is an important skill for a new developer to obtain and build gradually.

Don't worry. We will help you out a bit.

As you already identified the problem above, the next step is to critically think about Schema - how and what data we want to record in our database.

You will need 2 Schemas: User and Task.

# User Schema:

User is created by name, so there must be a nam field in User schema. This is mandatory (required)
User has two roles: manager and employee => a role field in User with String type and we need enum validator for its value. more
The enum validator is an array that will check if the value given is an item in the array. If the value is not in the array, Mongoose will throw an error.

# Task Schema:

A task should contain the field name and description for the basic information. Can a task have no name and no description? For now, let's make them mandatory.

The task status is tricky. Let's say you have decided there are 5 types of values for the status field: pending, working, review, done, archive.

pending: work not started
working: is working on it
review: waiting for review result
done : review is finished with satisfaction
archive: package as references for future
Key note from requirements

A user may have one, many, or no task he/she is responsible for.
A task may have one or no one asign to it yet
