# The Complete Oracle SQL Bootcamp

### What is a database?

A database is an organized collection of data that is stored and accessed electronically. It allows users and applications to efficiently store, retrieve, update and manage data.

Key Concepts:

- Structured Format: Data is typically organized in tables (row and columns) when using relational database.
- DBMS (Database Management System): Software like MySQL, PostgreSQL, Oracle or MongoDB that manages the database.
- Query Language: Most databases use languages like SQL (Structures Query Language) to interact with data.

There are few types of DBMS:

- Hierarchical DBMS
- Relational DBMS
- Network DBMS
- Object-Relational DBMS

Example:
In a relational database for a school:

- A "Students" table might store data like:

```
ID | Name      | Grade
---|-----------|------
1  | Alice     | A
2  | Bob       | B
```

Types of databases:

- Relational Databases (MySQL, PostgreSQL)
- NoSQL Databases (MongoDB, Redis)
- In-Memory Databases (Redis)
- Cloud Databases (Amazon RDS, Firebase)
- Graph Database (Neo4j)

Uses:

- Websites and apps (User info, products)
- Banking Systems
- Healthcare records
- Scientific research
- Business analytics

* DB Engines Ranking: https://db-engines.com/en/ranking

### Why Oracle Database?

Oracle database is one of the most popular and powerful database management systems in the world. Organizations choose oracle for many reasons, especially when they need high performance, security, scalability and advanced features.

Why Oracle Database?

1. High Performance & Scalability

- Optimized for large-scale enterprise applications.
- Can handle huge volumes of data and millions of transactions per second
- Offers Real Application Clusters (RAC) for horizontal scaling.

2. Robust Security

- Built-in features like data encryption, auditing, user role management, and label-based security
- Compile with enterprise and government regulations

3. Advanced Features

- PL/SQL: Oracle's powerful procedural extension to SQL for writing complex business logic
- Partitioning: Allows large tables to be split for better performance
- Materialized Views: For fast query performance on large datasets
- Flaskback Technology: Lets you recover data to a previous state without restore operations

4. Reliability & Availability

- Data Guard: For disaster recovery and high availability
- Automatic Storage Management (ASM): Simplifies storage management and improves performance

5. Cross-platform Compatibility

- Works on Linux, Windows, UNIX and more
- Supports integration with many development platforms (Java, .NET, Python, etc)

6. Enterprise Support & Tools

- Oracle provides robust support, documentations and tools (Oracle SQL Developer, APEX)
- Strong ecosystem for backup, monitoring, tuning and data replication

Use Cases:

- Banking & Finance: Complex transactions, security
- Telecommunications: Real-time data management
- Goverment System: Compliance-heavy workloads
- Enterprise ERP/CRM: Oracle is the backend for many SAP and Oracle applications

When not to use oracle?

- For small projects or startups, Oracle can be costly and complex
- Alternatives like PostgreSQL or MySQL may be better for lighter workloads

### What is a table?

A table in a database is a structured way to store data in rows and columns, similar to a spreadsheet. Each table represents one type of entity (students, products, employees) and each row represents a single record of that entity.

Structure of a table:

- Columns: Define the types of data (like name, age, date)
- Rows: Contain actual data entries (records)
- Fields: The intersection of a row and a column (a single data value)
- Primary Key: A column (or combination of columns) that uniquely identifies each row

Example: Students Table

| ID  | Name    | Age | Grade |
| --- | ------- | --- | ----- |
| 1   | Alice   | 14  | A     |
| 2   | Bob     | 15  | B     |
| 3   | Charlie | 14  | A     |

- Table name: Students
- Column: ID, Name, Age, Grade
- Row 1: Represents the student Alice
- Primary Key: ID (each student has a unique id)

Why Tables?

- Tables organize data clearly and logically
- They support relationships between different data sets (via keys)
- Easy to query, update and manage using SQL

### What is Relational Database RDBMS?

A Relational Database Management System (RDBMS) is a type of software used to create, manage and interact with relational databases, where data is organized into tables with rows and columns and relationships between tables are defined using keys.

What makes it "Relational"?
The "relational" part means:

- Data is stored in related tables
- Tables can be linked using foreign keys
- Can retrieve complex data using SQL joins.

Example
Table: Students
| StudentID | Name |
| --------- | ----- |
| 1 | Alice |
| 2 | Bob |

Table: Courses
| CourseID | Title |
| -------- | ------- |
| 101 | Math |
| 102 | Science |

Table: Enrollments
| StudentID | CourseID |
| --------- | -------- |
| 1 | 101 |
| 2 | 102 |

- This shows that Alice is enrolled in Math, and Blob is enrolled in Science
- The relationship is defined by lining StudentID and CourseID

Key features of RDBMS:

- Tables: Organize data into rows and columns
- SQL Support: Structured Query Language used to query and manage data
- Primary Keys: Uniquely identify each record in a table
- Foreign Keys: Define relationships between tables
- ACID Compliance: Ensures data atomicity, Consistency, Isolation and Durability
- Data Integration: Enforces rules for accuracy and consistency
- Concurrency Control: Manages multiple users accessing data at the same time.

Common RDBMS Software:

- Oracle Database
- MySQL
- PostgreSQL
- SQL Server
- IBM Db2

### Entity Relationship Logic in Database

Entity-Relationship (ER) logic in a database is a way to model the structure of data by identifying:

- Entity: Things or objects want to store data about
- Attributes: The data store about those things
- Relationship: How those things are connected

This logic is usually captured in an Entity-Relationship Disgram (ERD), which is the foundation of relational database design.

1. Entity
   An entity is a real-world object or concept that can be stored in the database.
   Example:

- Student
- Course
- Employees
- Department
  Entities usually become tables in the database.

2. Attribute
   An attribute is a property or characteristic of entity.
   Example: For the Student entity

- StudentID (Primary Key)
- Name
- DateOfBirth
- Email
  Attributes become columns in the table

3. Relationship
   A relationship is a connection between two or more entities.
   Types of relationship:

- One-to-one: One Employee has one Office (Each row in one table is linked to one row in another table)
- One-to-many: One Teacher teaches many Courses (A row in one table can link to many rows in another table)
- Many-to-many: Many Students enrolled in many Courses (Requires a junction table, e.g. Enrollments)

ER Diagram Example:
Entities:

- Student
- Course
- Enrollment (a junction table for many-to-many)

Relationships:

- A student can enroll in many courses
- A course can have many Students

ER Diagram:
Student --------< Enrollment >-------- Course

4. Keys in Relationships

- Primary Key: Unique indentifies each record in a table
- Foreign Key: Connects one table to another, referencing its primary key

Example:
In Enrollment table:

- StudentID is a foreign key referencing Student(StudentID)
- CourseID is a foreign key referencing Course(CourseID)

Why ER Logic in important:

- Helps design normalized database (avoid redundancy)
- Ensures data consistency
- Makes querying relationships efficient using JOINS
- Aids in communication between business and technical teams

### What is Pluggable Database?

A Pluggable Database (PDB) is a feature of Oracle Multitenant Architecture introduced in Oracle Database 12c that allows a single Oracle database container (CDB) to hold multiple independent databases (PDBs) within it.

A Pluggable Database (PDB) is a portable, self-contained database that runs inside a Container Database (CDB). It has its own data, users and objects but shares the Oracle instance (memory, processes) with other PDBs in the same container.

Architecture Overview:

- CDB (Container Database):
  - The overall Oracle database instance
  - Contains:
    - One Root container (CDB$ROOT) - Stores common metadata and system users.
    - One Seed PDB (PDB$SEED) - a template to create new PDBs.
    - One or more Pluggable Databases (PDB1, PDB2,...) - user-defined databases.
      +---------------------------+
      | CDB (Oracle DB) |
      | +--------+ +----------+ |
      | | CDB$ROOT|  | PDB$SEED | |
      | +--------+ +----------+ |
      | +--------+ +----------+ |
      | | PDB1 | | PDB2 | |
      | +--------+ +----------+ |
      +---------------------------+

Key Features of Pluggable Databases:

- Isolation: Each PDB is logically independent
- Portability: Can unplug a PDB from one CDB and plug it into another
- Rapid Provisioning: Clone from PDB$SEED or existing PDBs quickly.
- Consolidation: Run many databases with lower resource usage
- Centralized Management: Manage many PDBs from a single CDB

Use cases:

- Multi-tenant SaaS applications (Obe PDB per customer)
- Development and testing environments (easy cloning)
- Efficient consolidation of many small databases
- Cloud deployments (like Oracle Autonomous Database)

Security Note:

- PDBs are logically isolated, but share the same Oracle instance. Use proper privileges and roles to maintain secure boundaries

Example SQL to Create a New PDB:

```
CREATE PLUGGABLE DATABASE pdb1
ADMIN USER pdbadmin IDENTIFIED BY mypassword
FILE_NAME_CONVERT = ('/u01/app/oracle/oradata/CDB1/pdbseed/',
                    '/u01/app/oracle/oradata/CDB1/pdb1/');
```

### Introduction to database objects

In a database, objects are the components that store and manage data, define its structure, and control its behavior. They are created and managed using SQL commands.

Common Database Objects:

- Table: Stores data in rows and columns
- View: A virtual table based on a query
- Index: Improves the speed of data retrieval
- Sequence: Automatically generates numeric values (e.g. for primary key)
- Synonym: An alias for another database object (often for tables or views)
- Procedure: A stored block of code that performs on action
- Function: Similar to a procedure but returns a value
- Trigger: Code that executes automatically in response to events (e.g. insert, update)
- Package: A group of related procedures, functions and variables
- Constraint: Rules to enforce data integrity (e.g. PRIMARY KEY, FOREIGN KEY)
- User / Schema: Represents the owner of database objects and defines access

1. Table

- Main structure for storing data
- Has columns and rows

```
CREATE TABLE employees (
  emp_id NUMBER PRIMARY KEY,
  name VARCHAR2(50),
  salary NUMBER
);
```

2. Views

- A saved SQL query that shows data from one or more tables

```
CREATE VIEW high_salary_emps AS
SELECT name, salary FROM employees WHERE salary > 50000;
```

3. Index

- Speeds up data lookup (like an index in book)

```
CREATE INDEX emp_name_idx ON employees(name);
```

4. Sequence

- Auto-generated unique numbers (often for primary keys)

```
CREATE SEQUENCE emp_seq START WITH 1 INCREMENT BY 1;
```

5. Synonym

- Alias to simplify access to other objects

```
CREATE SYNONYM emp FOR HR.employees;
```

6. Stored Procedure

- A reusable block of PL/SQL code that performs a task

```
CREATE PROCEDURE raise_salary (id NUMBER, amount NUMBER) AS
BEGIN
  UPDATE employees SET salary = salary + amount WHERE emp_id = id;
END;
```

7. Function

- Similar to a procedure but returns a value

```
CREATE FUNCTION get_salary (id NUMBER) RETURN NUMBER AS
  s NUMBER;
BEGIN
  SELECT salary INTO s FROM employees WHERE emp_id = id;
  RETURN s;
END;
```

8. Trigger

- Automatically runs before or after certain events (INSERT, UPDATE, DELETE).

```
CREATE TRIGGER log_salary_update
AFTER UPDATE OF salary ON employees
FOR EACH ROW
BEGIN
  INSERT INTO salary_log (emp_id, old_salary, new_salary)
  VALUES (:OLD.emp_id, :OLD.salary, :NEW.salary);
END;
```

9. Package

- Groups multiple procedures, functions, variables together.

```
CREATE PACKAGE emp_tools AS
  PROCEDURE hire_employee(...);
  FUNCTION calc_bonus(...);
END;
```

10. Constraint

- Rules that ensure data integrity.

```
CREATE TABLE dept (
  dept_id NUMBER PRIMARY KEY,
  name VARCHAR2(50) UNIQUE
);
```

### What is a Schema?

A schema is a logical container in a database that holds all the related database objects - such as tables, views, indexes, procedures and more - that belong to a specific user or application.

A schema is like a folder in a database, and the database objects (tables, views, etc) are the files inside it.

Example:
Suppose have a user named hr. The hr schema might include:
hr.employees (table), hr.departments (table), hr.get_salary() (function), hr.salary_log (table).
Here hr is both the username and the schema name.

Schema vs Database (especially in oracle)

- Schema: In oracle - Owned by a user account, holds objects, In MySQL/PostgreSQL - A namespace within a database.
- Database: In oracle - A collection of schemas (CDBs, PDBs), In MySQL/PostgreSQL - One main logical container

- In Oracle, one user = one schema
- In PostgreSQL, one database can have multiple schemas

Why use schemas?

- Organization - Group related objects (HR, Sales, etc)
- Security - Control access per schema/user
- Reusability - Same object name in different schemas
- Namespace separation - Avoid object name collisions

Example SQL:

```
CREATE USER sales IDENTIFIED BY password;

GRANT CONNECT, RESOURCE TO sales;

CREATE TABLE sales.customers (
  id NUMBER PRIMARY KEY,
  name VARCHAR2(100)
);
```

<img src="../images/6.png" height="auto" width="auto" />

### What is SQL?

SQL (Structured Query Language) is the standard language used to communicate with relational databases. It allows to create, read, update, and delete (CRUD) data, as well as manage database structure and control access.

SQL = Structured Query Language

What can SQL do?

- Data Query - Retrieve data - SELECT \* FROM employees;
- Data Insertion - Add new records - INSERT INTO employees (...) VALUES (...);
- Data Update - Modify existing data - UPDATE employees SET salary = 5000 WHERE id = 1;
- Data Deletion - Remove records - DELETE FROM employees WHERE id = 1;
- Table Creation - Define tables and structure - CREATE TABLE employees (...);
- Access Control - Manage users and permissions - GRANT SELECT ON employees TO user1;

Common Categories of SQL Commands:

- DDL (Data Definition Language): Defines database structure (CREATE, ALTER, DROP)
- DML (Data Manipulation Language): Handles data inside tables (SELECT, INSERT, UPDATE, DELETE)
- DCL (Data Control Language): Controls user access (GRANT, REVOKE)
- TCL (Transaction Control Language): Manage Transactions (COMMIT, ROLLBACK, SAVEPOINT)

```
-- Create a table
CREATE TABLE employees (
  id NUMBER PRIMARY KEY,
  name VARCHAR2(100),
  salary NUMBER
);

-- Insert data
INSERT INTO employees (id, name, salary) VALUES (1, 'Alice', 5000);

-- Read data
SELECT * FROM employees;

-- Update data
UPDATE employees SET salary = 6000 WHERE id = 1;

-- Delete data
DELETE FROM employees WHERE id = 1;
```

Where is SQL used?

- Relational Databases: Oracle, MySQL, PostgreSQL, SQL Server
- Data Analysis: In BI tool (Power BI, tableau)
- Back-end Application: Web and mobile apps using SQL to store/retrieve data
- Enterprise Systems: Banking, HR, Inventory, E-Commerce

### Oracle Data Types

In Oracle Database, data types define the kind of data a column, variable, or expression can hold. Choosing the right data type is important for performance, storage, and accuracy.

1. Character Data Types

- CHAR(n): Fixed length string (Padded with space). Max 2000 bytes
- VARCHAR2(n): Variable length string. Most commonly used. Max 4000 bytes in SQL (more in PL/SQL)
- NCAHR(n): Fixed length unicode string
- NVARCHAR2(n): Variable length unicode string

```
name VARCHAR2(50);
```

2. Numeric Data Types

- NUMBER(p,s): General-purpose number. p=precision, s=scale
- INTEGER: Same as NUMBER(38, 0)
- FLOAT: Floating point number

```
salary NUMBER(8,2);
```

3. Date and Time Data Types

- DATE: Stores date and time (up to seconds)
- TIMESTAMP: More precise than DATE (can store fractional seconds)
- TIMESTAMP WITH TIME ZONE: Includes time zone info
- TIMESTAMP WITH LOCAL TIME ZONE: Converts time zone to users session time zone
- INTERVAL: Stores duration of time (e.g. 2days, 5hours)

```
hire_date DATE;
event_time TIMESTAMP(3);
```

4. Large Object (LOB) Data Type

- CLOB: Character large object (for large text)
- BLOB: Binary large object (for images, files)
- NCLOB: Unicode CLOB
- BFILE: Stores file pointers to external binary files (real-only)

```
article CLOB;
image_data BLOB;
```

5. Raw and Binary Data Types

- RAW(n): Stores binary data (up to 2000 bytes)
- LONG ROW: Variable length binary (up to 2GB, deprecated)

6. ROWID and UROWID

- ROWID: Unique ID of a row in a table (physical address)
- UROWID: For both physical and logical row identifiers

### What is a NULL value?

In SQL (and in Oracle), a NULL value represents missing, unknown, or inapplicable data. It does not mean zero, empty string or false - it simply means the value is not known or not provided.

Key points about Null:

- Unknown: NULL indicates the absence of a value
- Not the same as 0 or '': NULL != 0 and NULL != ''
- Data Type: NULL can exist in any column type (text, number, date, etc)
- Affects logic: NULL makes logical comparisons tricky - NULL = NULL is not true.

Example:
Table: employees
| emp*id | name | salary |
| ------- | ----- | ------ |
| 1 | Alice | 5000 |
| 2 | Bob | \_NULL* |

- Bob's salary is unknown - that's why it's stored as NULL

NULL in conditions:

- salary = NULL: Always false
- salary IS NULL: True if NULL
- salary IS NOT NULL: True if NOT NULL

Correct Usage:

```
SELECR * FROM employees WHERE salary IS NULL;
```

NULL in Functions & Expressions:

- Most functions ignore NULLs unless handled specifically
- Example with SUM():

```
SELECT SUM(salary) FROM employees; -- Will ignore rows where salary is NULL
```

NULL and Equality

```
SELECT * FROM table WHERE column1 = column2; -- If either column is NULL, this condition is FALSE
```

Use NVL() (Oracle-specific) or COALESCE() to handle NULLs:

```
SELECT NVL(salary, 0) FROM employees; -- Replace NULL salary with 0
```

- NULL = unknown or missing data
- Use IS NULL / IS NOT NULL to check
- Avoid using = or <> with NULL
- NULLs can affect logic, joins, and aggregations

### DESCRIBE Command

The DESCRIBE (or DESC) command is used to display the structure of a table or view - including the column names, data types and whether a column allows NULL values.

```
DESCRIBE table_name;
-- OR
DESC table_name;
```

Output Columns:
| Name | Null? | Type |
| ---------- | -------- | ------------ |
| EMP_ID | NOT NULL | NUMBER(6) |
| NAME | | VARCHAR2(50) |
| SALARY | | NUMBER(8,2) |
| HIRE_DATE | | DATE |

- DESCRIBE is SQL\*PLUS and Oracle-specific. It works in:
  - Oracle SQL\*Plus
  - Oracle SQL Server
  - Some other tools like TOAD
- Not Standard SQL: Other databases like MySQL, PostgreSQL use different command (e.g. SHOW COLUMN, \d table, INFORMATION_SCHEMA queries)
