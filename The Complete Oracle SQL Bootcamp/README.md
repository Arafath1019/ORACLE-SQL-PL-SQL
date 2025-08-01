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
