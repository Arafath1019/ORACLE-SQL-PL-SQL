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

### Drop Table
```
$ DROP TABLE Employees;
```

### Truncate Table
```
$ TRUNCATE TABLE Employees;
```

### Constraints
* Is a rule to which data must be conform
* Constraint names are optional
* Can be added at Column level or Table Level
* Can be enabled/disabled/dropped
* Types of Constraints: NOT NULL, UNIQUE, PRIMARY KEY, CHECK, FOREIGN KEY

### NOT NULL Constraint
```
$ CREATE TABLE Sample1(
    Col1 number constraint Sample1_Col1_nn NOT NULL,
    Col2 number NOL NULL
);
$ ALTER TABLE Employees modify FirstName varchar2(20) constraint Employee_FirstName_NN NOT NULL;
```

### UNIQUE Constraint
<img src="../images/1.png" height="auto" width="auto" />

```
CREATE TABLE Sample2(
    Col1 NUMBER CONSTRAINT Sample2_Col1_un UNIQUE,
    Col2 NUMBER,
    Col3 NUMBER,
    CONSTRAINT Sample2_unique UNIQUE(Col2, Col3)
);
```

```
ALTER TABLE Employees ADD CONSTRAINT Employee_Email_un UNIQUE(EmailID);
```

### PRIMARY KEY Constraint
* Column Level Primary Key Constraint
```
CREATE TABLE Sample1(
    Col1 NUMBER CONSTRAINT Sample1_pk PRIMARY KEY,
    Col2 NUMBER,
    Col3 NUMBER
);
```
* TABLE Level Primary Key Constraint
```
CREATE TABLE Sample1(
    Col1 NUMBER,
    Col2 NUMBER,
    Col3 NUMBER,
    CONSTRAINT Sample1_pk PRIMARY KEY(Col1)
);
```
* ALTER TABLE
```
ALTER TABLE Sample1 ADD CONSTRAINT Sample1_pk PRIMARY KEY(Col1);
```

### CHECK CONSTRAINT
The CHECK constraint is used to limit the value range that can be placed in a column.
```
CREATE TABLE Sample1(
    Col1 NUMBER(10) CONSTRAINT Sample1_col1_check CHECK(Col1 >= 10000)
);
```
```
ALTER TABLE Employees ADD CONSTRAINT Emp_gender_check CHECK(gender in ('M', 'F'));
```

### FOREIGN KEY CONSTRAINT
<img src="../images/2.png" height="auto" width="auto" />

```
CREATE TABLE Departments(
    DEPTID NUMBER CONSTRAINT Departments_constraint_nn NOT NULL,
    DEPTNAME VARCHAR2(20)
);

CREATE TABLE Employees(
    EmpId NUMBER(3) CONSTRAINT Employees_empid_nn NOT NUL,
    FirstName VARCHAR2(20) CONSTRAINT Employees_firstname_nn NOT NULL,
    DeptId NUMBER,
    CONSTRAINT Employees_deptid_rel FOREIGN KEY(DeptId) REFERENCES Departments(DeptId) ON DELETE SET NULL
);

CREATE TABLE Employees(
    EmpId NUMBER(3) CONSTRAINT Employees_empid_nn NOT NUL,
    FirstName VARCHAR2(20) CONSTRAINT Employees_firstname_nn NOT NULL,
    DeptId NUMBER,
    CONSTRAINT Employees_deptid_rel FOREIGN KEY(DeptId) REFERENCES Departments(DeptId) ON DELETE CASECADE
);
```

```
ALTER TABLE Employees ADD CONSTRAINT Emp_dept_Rel FOREIGN KEY(DeptId) REFERENCES Departments(DeptId) ON DELETE SET NULL;
```

### Managing Constraints
* Add a constraint
```
ALTER TABLE customers ADD CONSTRAINT unique_email UNIQUE(email);
```
* Disable a constraint
```
ALTER TABLE customers DISABLE CONSTRAINT unique_email;
```
* Enable a constraint
```
ALTER TABLE customers ENABLE CONSTRAINT unique_email;
```
* Drop a constraint
```
ALTER TABLE customers DROP CONSTRAINT unique_email;
```

### Data Manipulation Language
* Add new rows to a table
* Modify existing rows in a table
* Remove existing rows from a table
* Multiple DML statements performing a logical task is called transaction
* Use COMMIT command to save the changes
* Use ROLLBACK command to undo the changes
* Statements: Insert, Update, Delete, Merge

### Insert Statement
```
INSERT INTO Customers(customer_id, first_name, last_name, age, country) VALUES(1, "Yeasin", "Arafath", 25, "BAN");
```

```
INSERT INTO Customers VALUES(1, "Yeasin", "Arafath", 25, "BAN");
```

```
INSERT INTO Customers VALUES(&customer_id, "&first_name", "&last_name", &age, "&country");

COMMIT; -> TO commit the changes
```

### Update Statement
```
UPDATE Employees SET DeptId = 30 WHERE EmpId = 101;

UPDATE Employees SET MobileNo = '123456789', LastName = 'Dubey', DateOfJoining = '20-Dec-16' WHERE EmpId = 102;
```

### DELETE STATEMENT
```
DELETE FROM Employees WHERE EmpId = 101;
```