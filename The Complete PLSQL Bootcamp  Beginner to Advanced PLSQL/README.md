# The Complete PL/SQL Bootcamp Beginner to Advanced PL/SQL

### What is PL/SQL
* PL/SQL stands for Procedural Language/Structured Query Language
* It is Oracle's extension of SQL - meaning it adds programming features to normal SQL
* SQL can only query and manipulate data
* PL/SQL can do loops, conditions, functions, procedures, error handling etc
* PL/SQL -> SQL + Procedural Programming
* Platform Independence (Mac, Windows, Linux)

### Why use PL/SQL
* Group multiple SQL statements together
* Add Login (IF, FOR, WHILE)
* Performance
* Error Handling
* Reusability
* Security

### PL/SQL Architecture
The architecture in two parts, Physical Architecture and Logical Architecture.
Physical Architecture:
When PL/SQL code executes, it interacts with:
* SQL Engine (To handle SQL statements)
* PL/SQL Engine (To handle PL/SQL Code)
* Database Server (To Store and Fetch Data)

How it works Step-by-step:
* Submit a PL/SQL block
* PL/SQL engine checks the block, if it's PL/SQL logic, executes immediately, if it's a SQL statement, sends it to the SQL engine
* SQL engine handle the SQL, return the result to PL/SQL if needed.
* PL/SQL engine continues the running
* Results are returned or stored

* Diagram
```
    PL/SQL Block
        ↓
   PL/SQL Engine
       /    \
(PL/SQL logic) (SQL Statements)
     ↓              ↓
Execute        SQL Engine
                  ↓
          Database Server
```

Logical Architecture:
* Cooperates with SQL engine
* Enables subprograms
* Dynamic Queries
* Case Insensitivity
* Optimizer
* Enable Object Oriented Programming

### The Sample (HR) Schema 
* What is Schema?
=> Schemas are the collection of objects for each user in Oracle Database. In Oracle Database, a schema is a collection of database objects that belong to a specific user. These objects can include tables, views, indexes, sequences, procedures, functions, packages, and other structures. Each user account in Oracle has its own schema, and the schema name is the same as the username.

* A schema is a logical container for objects created by a user
* It helps organize and manage database objects
* Access to objects in a schema can be controlled through permissions.

For example, if a user named HR creates a table called EMPLOYEES, the fully qualified name of the table would be HR.EMPLOYEES, indicating that the EMPLOYEES table belongs to the HR schema. 

<img src="../images/6.png" height="auto" width="auto" />