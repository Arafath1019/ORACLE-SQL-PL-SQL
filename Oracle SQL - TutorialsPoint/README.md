# Oracle SQL - TutorialsPoint

### What is Database?
* Provides permanent storage of data
* Is a collection of different database objects
* Different objects have different roles to perform
* Refers to a set of related data and the way it is organized

### What is DBMS?
* DBMS is a computer software application that interacts with the user, other applications to capture and analyze data
* Is designed to allow the definition, creation, querying, update and administration of databases
* Data sharing, data security, data integration, data access are some the major advantages of dbms

### What is RDBMS?
* Is a database with relational model
* Developed by E.F. Codd
* RM purpose is to provide a declarative method for specifying data queries
* Most relational database use the SQL

### SQL
* Stands for Structured Query Language
* Designed by Donald Chamberlin and Raymond Boyce in 1974
* Is a special-purpose language designed for managing data held in a RDBMS
* Is a forth generation language
* Can be classified in several types on the basis of task performed

### CLassification of SQL
* DDL - Data Definition Language
* DML - Data Manipulation Language
* DRL - Data Retrieval Language
* DCL - Data Control Language
* TCL - Transaction Control Language

### Introduction to Oracle
* Founded by Larry Ellison with Bob Miner and Ed Oates in 1977
* Deals with the Databases, Middleware, Business Apps, Development Softwares, File Systems, Operating Systems, etc.

### Environment Setup
* Download and install Orcale Database from oracle.com
* Oracle Database online compiler: https://www.programiz.com/sql/online-compiler/

### Getting Started
```
$ sqlplus (it is a command line tool that allows to access and interact with oracle database)
Enter user-name: sys/system
Enter Password: Password provided while installation

$ disc (Disconnect from the database)
$ conn sys as sysdba (connecting with database with sys user as sysdba)

$ show user (show the connected user)
```

### DDL (Data Definition Language) Statement
* Create (Create any database object)
* Alter (Update any database object structure)
* Drop (Delete database object)
* Truncate (To delete all the data from a table)
* Rename (Rename any particular database object)

### Create Table
* Can be classified in Data Dictionary and User Tables
* Must give a valid Table name
* User must have a create table permission and storage area
* Table will be created in user's schema
* DEFAULT keyword is used to set default value for the column

```
$ CREATE TABLE Employees(
    EmpId number,
    FirstName varchar2(20),
    LastName varchar2(20),
    EmailId varchar2(50),
    Gender char(1),
    MobileNo char(10),
    DateOfJoining date default sysdate,
    DeptId int
);
```

### Alter Table
* Adding column
* Modifying column
* Dropping column
* Renaming column

```
# Add new column in table
$ ALTER TABLE Employees add DOB date;
$ ALTER TABLE Employees add (Salary number(10,2), Col1 number);

# Change datatype of any column
$ ALTER TABLE Employees modify Col1 varchar2(10);

# Delete column
$ ALTER TABLE Employees DROP COLUMN Salary;
$ ALTER TABLE Employees SET UNUSED COLUMN Col1;
$ ALTER TABLE Employees DROP UNUSED columns;
```