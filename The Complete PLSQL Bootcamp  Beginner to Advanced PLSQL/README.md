# The Complete PL/SQL Bootcamp Beginner to Advanced PL/SQL

### What is PL/SQL

- PL/SQL stands for Procedural Language/Structured Query Language
- It is Oracle's extension of SQL - meaning it adds programming features to normal SQL
- SQL can only query and manipulate data
- PL/SQL can do loops, conditions, functions, procedures, error handling etc
- PL/SQL -> SQL + Procedural Programming
- Platform Independence (Mac, Windows, Linux)

### Why use PL/SQL

- Group multiple SQL statements together
- Add Login (IF, FOR, WHILE)
- Performance
- Error Handling
- Reusability
- Security

### PL/SQL Architecture

The architecture in two parts, Physical Architecture and Logical Architecture.
Physical Architecture:
When PL/SQL code executes, it interacts with:

- SQL Engine (To handle SQL statements)
- PL/SQL Engine (To handle PL/SQL Code)
- Database Server (To Store and Fetch Data)

How it works Step-by-step:

- Submit a PL/SQL block
- PL/SQL engine checks the block, if it's PL/SQL logic, executes immediately, if it's a SQL statement, sends it to the SQL engine
- SQL engine handle the SQL, return the result to PL/SQL if needed.
- PL/SQL engine continues the running
- Results are returned or stored

- Diagram

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

- Cooperates with SQL engine
- Enables subprograms
- Dynamic Queries
- Case Insensitivity
- Optimizer
- Enable Object Oriented Programming

### The Sample (HR) Schema

- What is Schema?
  => Schemas are the collection of objects for each user in Oracle Database. In Oracle Database, a schema is a collection of database objects that belong to a specific user. These objects can include tables, views, indexes, sequences, procedures, functions, packages, and other structures. Each user account in Oracle has its own schema, and the schema name is the same as the username.

- A schema is a logical container for objects created by a user
- It helps organize and manage database objects
- Access to objects in a schema can be controlled through permissions.

For example, if a user named HR creates a table called EMPLOYEES, the fully qualified name of the table would be HR.EMPLOYEES, indicating that the EMPLOYEES table belongs to the HR schema.

<img src="../images/6.png" height="auto" width="auto" />

### About the database installation

1. Having with using VirtualBox
2. Installing Database into computer

### Which Option to Choose to Have a Database

Three Options to Have a Database

1. Using the VirtualBox Option
2. Installing Database into computer
3. Using Oracle Live SQL (https://livesql.oracle.com/landing/)

### Option 1 Having the Database with the Oracle Virtual Box

1. Download & Install Virtual Box: https://www.virtualbox.org/
2. Download Oracle VM with Database (Recommended for this tutorial): https://drive.usercontent.google.com/download?id=1JDM28LwcA_AvLAJyYJfLAOI6_4oLTMBn&export=download&authuser=0

Otherwise, Download Pre-Built Developer VMs (for Oracle VM VirtualBox) (Download Database App Development VM): https://www.oracle.com/downloads/developer-vm/community-downloads.html

3. Import Downloaded Machine to VirtualBox:
   Open VirtualBox -> File -> Import Appliance -> Select the downloaded machine -> Import

4. Run the imported virtual disk image. (If there is not full screen for the first time, restart it.)

5. For Oracle VM with Database virtual disk image, Username: oracle, password: oracle

6. For system schema, Username: system, password: oracle

### What is Pluggable Database

A pluggable database (PDB) in Oracle is a portable collection of schemas, schema objects and non-schema objects that appears to an Oracle client as a non-CDB(non-container database). However, it actually exists within a multitenant container database (CDB).

- A CDB(Container Database) can contain zero, one or many PDBs.
- Each PDB is isolated from others and can be plugged in or unplugged from a CDB.
- PDBs share the CDB's memory and background processes, but have their own data and metadata.
- This architecture makes it easier to manage, move and consolidate databases.

### Option 2 Downloading and Installing the Oracle Database

1. Download Required Version (19c, 11c, 21c etc) (Express Edition, Standard Edition, Exterprise Edition) Zip File of Oracle Database (https://www.oracle.com/database/technologies/oracle-database-software-downloads.html) & Extract the zip folder
2. Create a Folder inside C drive (Example: OracleApp) & Paste the extracted folder inside the OracleApp folder
3. Open setup.exe & Install the Oracle data

### Option 2 Unlocking the HR Schema

Open Command Terminal & run the below commands:

1. `sqlplus / as sysdba;`
   Opens the SQL\*Plus command line tool and connects to the oracle database as a privileged user (SYSDBA), allowing you to perform administrative tasks.
2. `alter session set container=orclpdb;`
   Switches current session to the pluggable database named orclpdb, so that subsequent commands affect this specific PDB
3. `alter pluggable database open;`
   Opens the pluggable database (PDB) so it becomes available for use (accepts connections and operations).
4. `alter pluggable database orclpdb save state;`
   Saves the current open/closed state of the PDB (orclpdb), so it will automatically open in the same state after a database restart.
5. `alter user hr identified by hr account unlock;`
   Unlocks the HR user account and sets its password to hr, making it possible to log in as HR.
6. `/`

### Option 2 Configuring and Using the SQL Developer

1. Download Oracle SQL Developer Zip folder & Unzip the folder (https://www.oracle.com/database/sqldeveloper/technologies/download/)
2. Open sqldeveloer.exe from the folder
3. Create a database connection using the below ways

- Provide the information: Name, username, password, Connection type(Basic), Hostname, Port, Service name
- Provide the information: Name, username, password, Connection Type(TNS), Network Alias

4. sys user: It is the default superuser account. It owns all the base tables and views for the database's data dictionary. SYS has the highest level of privileges and is used for critical database administration tasks. SYS = main superuser, owns core database structures.
5. SYSTEM user: It is another administrative account. It owns additional tables and views used for database management and internal tools, but not for the core data dictionary. SYSTEM = administrative user, used for general database management.

### Option 3 Using Oracle Live SQL

1. Oracle Live SQL: https://livesql.oracle.com/landing/
