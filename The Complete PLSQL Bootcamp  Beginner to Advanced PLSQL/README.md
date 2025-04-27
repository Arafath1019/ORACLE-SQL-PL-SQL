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