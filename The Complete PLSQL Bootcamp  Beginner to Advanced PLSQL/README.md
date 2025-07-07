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

### Blocks

- What are blocks?
  -> In PL/SQL, a block is the basic unit of code. It is a group of related declarations and statements that are executed together. Every PL/SQL program is made up of one or more blocks.

A PL/SQL block has three main sections:

- Declaration Section (Optional): Where declare variables, constants, cursors, etc.
- Execution Section (mandatory): Where write the executable statements (logic, SQL, etc).
- Exception handling Sections (optional): Where handle errors or exceptions

The general structure is:

```
DECLARE
   -- Declarations (optional)
BEGIN
   -- Executable statements (mandatory)
EXCEPTION
   -- Exception handling (optional)
END;
```

Three types of blocks:

- Anonymous Blocks
- Procedures
- Functions

### PL/SQL Outputs

In PL/SQL, outputs refer to the results or information produced by executing a PL/SQL blocks. The most common ways to produce output in PL/SQL are:

1. DBMS_OUTPUT.PUT_LINE:
   This built-in procedure displays text output to the screen. It is mainly used for debugging or showing messages.

```
SET SERVEROUTPUT ON;

BEGIN
   DBMS_OUTPUT.PUT_LINE('Hello, World!');
END;
```

2. SELECT statements:
   When used in a PL/SQL block, SELECT statements can fetch data into variables, but they do not directly display output unless combined with DBMS_OUTPUT

3. OUT parameters:
   Procedures and functions can return values to the caller using OUT or IN OUT parameters.

4. RETURN statement:
   Functions return a value using the RETURN statement

5. EXCEPTIONS:
   When an error occurs, PL/SQL can output error messages using exception handling and DBMS_OUTPUT

### Nested Blocks:

In PL/SQL, nested blocks are PL/SQL blocks placed inside other PL/SQL blocks. This allows to structure code with inner blocks that have their own declarations, logic and exception handling, separate from the outer block.

- Inner (bested) blocks can access variables declared in the outer block, but not vice versa
- Each block can have its own exception section
- Useful for organizing code, limiting the scope of variables, and handling exceptions locally.

```
SET SERVEROUTPUT ON;
DECLARE
   outer_var NUMBER := 10;
BEGIN
   DBMS_OUTPUT.PUT_LINE('Outer block: ' || outer_var);

   DECLARE
      inner_var NUMBER := 20;
   BEGIN
      DBMS_OUTPUT.PUT_LINE('Inner block: ' || inner_var);
      DBMS_OUTPUT.PUT_LINE('Accessing outer_var from inner block: ' || outer_var);
   END;

   -- inner_var is not accessible here
   -- DBMS_OUTPUT.PUT_LINE(inner_var); -- This would cause an error
END;
```

### What are variables?

In PL/SQL, variables are named storage locations that hold data values during the execution of a program & can assign, change and use their values in code.

### Why do we need variables?

- To temporarily store data for processing (such as numbers, text, dates, etc)
- To hold results from queries or calculations
- To make code flexible and reusable by allowing values to change during execution
- To pass data between different parts of a program (such as between blocks, procedures, or functions)

### PL/SQL Variable Types:

1. Scalar Types: Store a single value
   - NUMBER: For numeric values (integers, decimals)
   - VARCHAR2, CHAR: For character strings
   - DATE, TIMESTAMP: For date and time values
   - BOOLEAN: For logical values (TRUE, FALSE, NULL)
2. Composite Types: Store multiple values or a collection
   - RECORD: A group of related data items (like a row)
   - TABLE, VARRAY, NESTED TABLE: Collections of elements (arrays/lists)
3. REFERENCE TYPES:
   - CURSOR: Used to handle query result sets
   - REF CURSOR: Pointer to a cursor
4. LOB Types:
   - BLOB, CLOB, NCLOB: For large binary or character data

### Variable Naming Rules:

- The name must begin with a letter
- It can include letters, numbers, and the symbols \_, $, $
- Maximum length is 30 characters
- Names are not case-sensative (myVar and MYVAR are the same)
- Cannot use reserved words like SELECT, BEGIN, etc
- Avoid starting with PL/SQL reserved prefixes (like "SYS\_")

### Naming Conventions

- VARIABLE(v_variable_name): v_max_salary
- CURSOR(cur_cursor_name): cur_employees
- EXCEPTION(e_exception_name): e_invalid_salary
- PROCEDURE(p_procedure_name): p_calculate_salary
- BIND VARIABLE(b_bind_name): b_emp_id

### Declaring & Initializing & Using Variables

General Usage:
`Name [CONSTANT] datatype [NOT NULL] [:= DEFAULT value|expression]`

Examples:

```
-----------------------===================-----------------------
-----------------------DECLARING VARIABLES-----------------------
-----------------------===================-----------------------
SET SERVEROUTPUT ON;
DECLARE
    v varchar2(20) := 2 + 25 * 3;
BEGIN
    dbms_output.put_line(v);
END;
-----------------------===================-----------------------
DECLARE
    v_text varchar2(50) NOT NULL DEFAULT 'Hello';
    v_number1 number := 50;
    v_number2 number(2) := 50.42;
    v_number3 number(10,2) := 50.42;
    v_number4 PLS_INTEGER := 50;
    v_number5 BINARY_float := 50.42;
    v_DATE1 DATE := '22-NOV-18 12:01:32';
    v_DATE2 timestamp := systimestamp;
    v_DATE3 timestamp(9) WITH TIME ZONE := systimestamp;
    v_DATE4 interval day(4) to second (3) := '124 02:05:21.012 ';
    v_DATE5 interval year to month := '12-3';
BEGIN
    V_TEXT := 'PL/SQL' || 'Course';
    DBMS_OUTPUT.PUT_LINE(V_TEXT);
    DBMS_OUTPUT.PUT_LINE(v_number1);
    DBMS_OUTPUT.PUT_LINE(v_number2);
    DBMS_OUTPUT.PUT_LINE(v_number3);
    DBMS_OUTPUT.PUT_LINE(v_number4);
    DBMS_OUTPUT.PUT_LINE(v_number5);
    DBMS_OUTPUT.PUT_LINE(v_DATE1);
    DBMS_OUTPUT.PUT_LINE(v_DATE2);
    DBMS_OUTPUT.PUT_LINE(v_DATE3);
    DBMS_OUTPUT.PUT_LINE(v_DATE4);
    DBMS_OUTPUT.PUT_LINE(v_DATE5);
    END;
----------------==================================---------------
----------------USING BOOLEAN DATA TYPE in PL/SQL----------------
----------------==================================---------------
DECLARE
    v_boolean boolean := true;
BEGIN
    dbms_output.put_line(sys.diutil.bool_to_int(v_boolean));
END;
----------------==================================---------------
```

\*\*\* DATE, TIMESTAMP, TIMESTAMP WITH TIME ZONE & INTERVAL

### USING %TYPE ATTRIBUTE

IN PL/SQL, the %TYPE attribute is used to declare a variable with the same data types as a column in a table or as another variable. This ensures that variable always matches the column's or variable's data type, even if the table definition changes later.

```
DECLARE
   V_TYPE employees.job_id%TYPE;
   V_TYPE2 V_TYPE%TYPE;
BEGIN
   V_TYPE := 'IT PROG';
   V_TYPE2 := 'SAM';
END;
```

### Delimiters & Commenting in Code

Delimiters:

- A PL/SQL block starts with DECLARE, then BEGIN and ends with END.
- Each statement inside the block ends with a semicolon
- String literals are enclosed in single quotes ('example')
- Parentheses () are used for grouping and function/procedure calls
- Commas separate items in lists
- - (Addition), - (Subtraction | Negation), \* (Multiplication), / (Division), = (Equality), @ (Remote Access), ; (Statement), <> (Inequality), != (Inequality), || (Concatenation), := (Assignment), -- (Single line comment), /\*\*/ (Multi line comment)

### PL/SQL variable scope

In PL/SQL, variable scope refers to where a variable can be accessed or used within code.

- A variable declared in the outer block is accessible in all its inner blocks
- A variable declared in an inner block is only accessible within that inner block - not in the outer block.
- If a variable with the same name is declared in both an outer and an inner block, the block's variable takes precedence (local scope)

This means:

- Outer block variables have wider scope within the block and its sub blocks
- Inner block variables have a local scope, limited to the block where they are declared.

```
SET SERVEROUTPUT ON;
DECLARE
   v_outer NUMBER := 100; -- Outer block variable
BEGIN
   DBMS_OUTPUT.PUT_LINE('Outer block: v_outer = ' || v_outer);

   DECLARE
      v_inner NUMBER := 200; -- Inner block variable
      v_outer NUMBER := 300; -- This shadows the outer v_outer
   BEGIN
      DBMS_OUTPUT.PUT_LINE('Inner block: v_inner = ' || v_inner);
      DBMS_OUTPUT.PUT_LINE('Inner block: v_outer = ' || v_outer); -- Refers to inner v_outer
   END;

   -- v_inner is not accessible here
   -- DBMS_OUTPUT.PUT_LINE(v_inner); -- This would cause an error

   DBMS_OUTPUT.PUT_LINE('Outer block again: v_outer = ' || v_outer); -- Refers to outer v_outer
END;
```

### Bind Variable

A bind variable in PL/SQL is a variable that is declared and used outside the PL/SQL block, typically in tools like SQL\*Plus, SQL Developer or application code. Bind variable allow to pass values into and out of PL/SQL blocks, procedures, or SQL statement at runtime.

- Bind variables are prefixed with a colon (:b_emp_id)
- They are defined in the host environment, not inside the PL/SQL block.
- They help improve performance by allowing SQL statements to be reused with different values, and they help prevent SQL injection.

```
VARIABLE b_emp_id NUMBER;

BEGIN
   :b_emp_id := 101;
END;
/

SELECT first_name from employees WHERE employee_id = :b_emp_id;
```

### What are control structures and if statements?

In PL/SQL, control structures are programming constructs that control the flow of execution in code. The main types are:

1. Conditional control (IF statements): Used to execute code only if certain conditions are true
2. Iterative control (Loops): Used to repeat a block of code multiple times (FOR, WHILE Loop)
3. Sequential Control (GOTO, EXIT): Used to change the normal sequence of execution

IF statements are a type of conditional control structure. They allow to execute certain statements only when a condition is true.

```
IF condition1 THEN
   --- statements
ELSIF condition2 THEN
   --- statements
ELSE
   --- statements
END IF;
```

```
SET SERVEROUTPUT ON;

DECLARE
   v_salary NUMBER := 4000;
BEGIN
   IF v_salary > 5000 THEN
      DBMS_OUTPUT.PUT_LINE('Salary is above 5000');
   ELSIF v_salary = 5000 THEN
      DBMS_OUTPUT.PUT_LINE('Salary is exact 5000');
   ELSE
      DBMS_OUTPUT.PUT_LINE('Salary is below 5000');
   END IF;
END;
```

### AND, OR, NOT Logical Operators

In PL/SQL, AND, OR, and NOT are logical operators used in conditions (such as IF statements) to combine or reverse logical expressions.

- AND: Returns true if both conditions are true.
- OR: Returns true if at least one condition is true
- NOT: Reverses the logical value

```
IF salary > 3000 AND department_id = 10 THEN
   DBMS_OUTPUT.PUT_LINE('High salary in department 10');
END IF;

IF salary < 2000 OR department_id = 20 THEN
   DBMS_OUTPUT.PUT_LINE('Low salary or in department 20');
END IF;

IF NOT (salary = 5000) THEN
   DBMS_OUTPUT.PUT_LINE('Salary is not 5000');
END IF;
```

### Case Expression

In PL/SQL, CASE expressions are used to perform conditional logic, similar to IF-THEN-ELSE, but in a more compact form. They allow to return a value based on different conditions.

There are two types of CASE expressions:

1. Simple CASE expression:

```
CASE variable
   WHEN value1 THEN result1
   WHEN value2 THEN result2
   ELSE default_result
END
```

```
DECLARE
   grade CHAR := 'B';
   result VARCHAR2(20);
BEGIN
   result := CASE grade
      WHEN 'A' THEN 'Excellent'
      WHEN 'B' THEN 'Good'
      WHEN 'C' THEN 'Average'
      ELSE 'Needs Improvement'
   END;
   DBMS_OUTPUT.PUT_LINE('Result: ' || result);
END;
```

2. Searched CASE Expression:

```
CASE
   WHEN condition1 THEN result1
   WHEN condition2 THEN result2
   ELSE default_result;
END;
```

```
SET SERVEROUTPUT ON;

DECLARE
   score NUMBER := 78;
   grade VARCHAR2(20);
BEGIN
   grade := CASE
      WHEN score >= 90 THEN 'A'
      WHEN score >= 80 THEN 'B'
      WHEN score >= 70 THEN 'C'
      ELSE 'F'
   END;
   DBMS_OUTPUT.PUT_LINE('Grade: ' || grade);
END;
```

### What are loops - basic loops

In PL/SQL, loops are control structures that allow to repeatedly execute a block of code multiple times.

A basic loop (also called a simple or unconditional loop) repeats its statements until explicitly exit the loop using an EXIT or EXIT WHEN statement.

```
LOOP
   -- statements
   EXIT WHEN condition; -- or just EXIT;
END LOOP;
```

```
DECLARE
   counter NUMBER := 1;
BEGIN
   LOOP
      DBMS_OUTPUT.PUT_LINE('Counter: ' || counter);
      counter := counter + 1;
      EXIT WHEN counter > 5;
   END LOOP;
END;
```

### WHILE Loops

In PL/SQL, a WHILE loop repeatedly executes a block of code as long as a specified condition is true. The condition is checked before each iteration.

```
WHILE condition LOOP
   -- statements
END LOOP;
```

```
DECLARE
   counter NUMBER := 1;
BEGIN
   WHILE counter <= 5 LOOP
      DBMS_OUTPUT.PUT_LINE('Counter: ' || counter);
      counter := counter + 1;
   END LOOP;
END;
```

### FOR Loops

In PL/SQL, a FOR loop is used to execute a block of code a specific number of times. The loop variable automatically takes on each integer value in a specified range.

```
FOR counter IN [REVERSE] lower_bound..upper_bound LOOP
   -- statements
END LOOP;
```

```
DECLARE
   i number;
BEGIN
   FOR i IN 1..5 LOOP
      DBMS_OUTPUT.PUT_LINE('Counter: ' || i);
   END LOOP;
END;
```

```
FOR i IN REVERSE 5..1 LOOP
   DBMS_OUTPUT.PUT_LINE('Counter: ' || i);
END LOOP;
```

### Nested Loops & Loop labeling

In PL/SQL, nested loops are loops placed inside other loops. Can use them to perform repeated actions within each iteration of an outer loop. Loop labeling helps to identify and control specific loops, especially when using EXIT or CONTINUE statements to exit from or continue a particular loop.

```
<<outer_loop>>
FOR i IN 1..3 LOOP
   DBMS_OUTPUT.PUT_LINE('Outer loop: ' || i);

   <<inner_loop>>
   FOR j IN 1..2 LOOP
      DBMS_OUTPUT.PUT_LINE('Inner loop: ' || j);

      IF i = 2 AND j = 1 THEN
         EXIT outer_loop;
      END IF;
   END LOOP inner_loop;
END LOOP outer_loop;
```

### CONTINUE statement

In PL/SQL, the CONTINUE statement is used inside loops to skip the remaining statements in the current iteration and move to the next iteration of the loop. Can also use CONTINUE WHEN condition; to skip to the next iteration only when a specific condition is true.

```
CONTINUE;
--- or
CONTINUE WHEN condition;
```

```
DECLARE
   i number;
BEGIN
   FOR i IN 1..5 LOOP
      IF MOD(i, 2) = 0 THEN
         CONTINUE;
      END IF;
      DBMS_OUTPUT.PUT_LINE('Odd number: ' || i);
   END LOOP;
END;
```

With loop labeling

```
<<my_loop>>
FOR i IN 1..5 LOOP
   CONTINUE my_loop WHEN i = 3;
   DBMS_OUTPUT.PUT_LINE('i= ' || i);
END LOOP;
```

### GOTO statement

In PL/SQL, the GOTO statement allows to transfer control unconditionally to a labeled statement within the same block; It is rarely used in modern code because it can make programs harder to read and maintain, but it can be useful in certain situations.

```
GOTO label_name
----
<<label_name>>
   -- statements
```

```
DECLARE
   v_num NUMBER := 1;
BEGIN
   IF v_num = 1 THEN
      GOTO skip_section;
   END IF;

   DBMS_OUTPUT.PUT_LINE(' This will be skipped');

   <<skipped_section>>
   DBMS_OUTPUT.PUT_LINE('GOTO jumped to this line');
END;
```

### Operating With Selected Queries

- Why to use SQL in PL/SQL?

  - Use SQL in PL/SQL to combine the power of SQL for data manipulation (such as SELECT, INSERT, UPDATE, DELETE) with the procedural capabilities of PL/SQL (such as variables, loops, conditions, and error handling). This allows to:
  - Retrieve, modify and manage data in the database directly from PL/SQL code
  - Automate complex business logic that involves multiple SQL operations.
  - Improve performance by reducing the number of calls between application and database.
  - Handle exceptions and control flow around SQL statements.

- There are some issues?

  - Can't use DDL commands directly.
  - A block does not mean a transaction

- How to use SQL in PL/SQL/

```
SELECT columns|expressions
INTO variables|records
FROM table|tables
[WHERE condition]
```

```
SELECT column1, column2
INTO variable1, variable2
FROM table_name
WHERE condition;
```

```
DECLARE
   v_name employees.first_name%TYPE;
   v_id employees.employee_id%TYPE = 101;
BEGIN
   SELECT first_name
   INTO v_name
   FROM employees
   WHERE employee_id = v_id;

   DBMS_OUTPUT.PUT_LINE('Employee Name: ' || v_name);
END;
```

### Naming Convention & Ambiguities

- Naming Convention:
  - Use clear, descriptive names that indicate the purpose of the variable, cursor, exception, etc.
  - Prefixes are often used to indicate type or scope:
    - v\_ for variable (v_salary)
    - cur\_ for cursors (cur_employees)
    - e\_ for exceptions (e_not_found)
    - p\_ for procedure parameters (p_emp_id)
    - b\_ for bind variables (b_dept_id)
  - Use underscores to separate words in multi-word names (total_salary, start_date)
  - Use Uppercase for constants (MAX_LIMIT)
  - Avoid using reserved words or names that too generic (value, number)
- Ambiguities"
  - If a variable and a column have the same name in a SQL statement, Oracle treats the name as a column by default. To avoid ambiguity, use table aliases or different names.
  - In nested block, if a variable is declared with the same name as an outer block variable, the inner variable "shadows" the outer one within its scope.
  - Always use meaningful and distinct names to prevent confusion and accidental errors in code.

### DML Operations in PL/SQL

DML (Data Manipulation Language) operations are used to manipulate data in database tables. In PL/SQL, can use DML statements directly inside PL/SQL blocks to insert, update, delete or select data.

Common DML operations:

- INSERT: Add new rows to a table
- UPDATE: Modify existing rows in a table
- DELETE: Remove rows from a table
- SELECT ... INTO: Retrieve data from a table into PL/SQL variables

-- INSERT example

```
BEGIN
   INSERT INTO employees (employee_id, first_name, last_name) VALUE (999, 'John', 'Doe');
END;
```

-- UPDATE example

```
BEGIN
   UPDATE employees
   SET salary = salary * 1.1
   WHERE department_id = 10;
END;
```

-- DELETE example

```
BEGIN
   DELETE FROM employees
   WHERE employee_id = 999;
END;
```

-- SELECT INTO example

```
DECLARE
   v_salary employee.salary%TYPE;
BEGIN
   SELECT salary INTO v_salary
   FROM employees
   WHERE employee_id = 100;
   DBMS_OUTPUT.PUT_LINE('Salary: ' || v_salary);
END;
```

- DML statements in PL/SQL blocks are part of the current transaction. Can use COMMIT to save changes or ROLLBACK to undo them.
- Always handle exceptions for DML operations to manage errors gracefully.

### Sequences in PL/SQL

A sequence in Oracle is a database object that generates a sequence of unique numeric values, often used for auto-incrementing primary keys.. In PL/SQL, can use sequences to generate unique numbers for inserting into tables.

- How to use a sequence in PL/SQL:
  - Use sequence_name.NEXTVAL to get the next value in the sequence
  - Use sequence_name.CURRVAL to get the current value (after at least one NEXTVAL call in the session)

-- Assuming a sequence named emp_seq exists

```
DECLARE
   v_new_id NUMBER;
BEGIN
   v_new_id := emp_seq.NEXTVAL;
   INSERT INTO employees (employee_id, first_name, last_name)
   VALUES (v_new_id, 'John', 'Doe');
END;
```

- Sequences are independent of tables and can be used by multiple users.
- Useful for generating unique keys in multi-user environments.
- Can't use NEXTVAL or CURRVAL in the VALUES clause of a SELECT statement without inserting or updating data.

-- Creating a sequence

```
CREATE SEQUENCE emp_seq
   START WITH 1
   INCREMENT BY 1
   NOCACHE
   NOCYCLE;
```

### Simple Data Types Vs Composite Data Types

Simple Data Types (Scalar Types):

- Hold a single value
- Examples:
  - NUMBER (v_num NUMBER := 10)
  - VARCHAR2 (v_name VARCHAR2 := 'John')
  - CHAR
  - DATE
  - BOOLEAN
- Used for basic data storage and manipulation

Composite Data Types:

- Can hold multiple values or a collection of values
- Examples:
  - RECORD: A group of related data items, possibly of different types (like a row in a table)
  ```
  TYPE emp_rec IS RECORD (id NUMBER, name VARCHAR2(20));
  v_emp emp_rec;
  ```
  - TABLE, VARRAY, NESTED TABLE: Collections (array/lists) of elements.
  ```
  TYPE num_table IS TABLE OF NUMBER;
  v_nums num_table := num_table(1,2,3);
  ```
  - Used for handling complex data structures and sets of data

### PL/SQL Records

- What is a record?
  A record in PL/SQL is a composite data type that allows to group related data items of different types into a single unit, similar to a row in a table. Each field in a record can have a different data type, and can access each field individually.

Why use records?

- To handle entire rows of data easily.
- To group related variables together for better organization and readability.

How to define and use a record:

1. Define a record type:

```
TYPE emp_rec IS RECORD (
   emp_id NUMBER,
   emp_name VARCHAR2(50),
   salary NUMBER
);
```

2. Declare a variable of that record type:

```
v_employee emp_rec;
```

3. Assign values and access fields:

```
v_employees.emp_id := 101;
v_employees.emp_name := 'John Doe';
v_employees.salary := 5000;

DBMS_OUTPUT.PUT_LINE('Name: ' || v_employees.emp_name);
```

Example Using a table row:

```
DECLARE
   TYPE emp_rec IS RECORD(
      emp_id employees.employee_id%TYPE,
      emp_name employees.first_name%TYPE,
      salary employees.salary%TYPE
   );

   v_emp emp_rec;
BEGIN
   SELECT employee_id, first_name, salary
   INTO v_emp
   FROM employees
   WHERE employee_id = 100;
END;
```

### DML with Records

Can use Records to perform DML operations (SELECT, INSERT, UPDATE, DELETE) more efficiently, especially when dealing with entire rows of data.

1. SELECT INTO a Record
   Fetch a row from a table directly into a record:

```
DECLARE
   TYPE emp_rec IS RECORD (
      emp_id employees.employee_id%TYPE,
      emp_name employees.first_name%TYPE,
      salary employees.salary%TYPE
   );
   v_emp emp_rec;
BEGIN
   SELECT employee_id, first_name, salary
   INTO v_emp
   FROM employees
   WHERE employee_id = 100;

   DBMS_OUTPUT.PUT_LINE('Name: ' || v_emp.first_name || ', Salary: ' || v_emp.salary);
END;
```

2. INSERT Using a Record

```
DECLARE
   TYPE emp_rec IS RECORD (
      emp_id employees.employee_id%TYPE,
      emp_name employees.first_name%TYPE,
      salary employees.salary%TYPE
   );
   v_emp emp_rec;
BEGIN
   v_emp.emp_id := 200;
   v_emp.emp_name := 'Jane';
   v_emp.salary := 6000;

   INSERT INTO employees (emp_id, emp_name, salary)
   VALUES (v_emp.emp_id, v_emp.emp_name, v_emp.salary);
END;
```

3. Update Using a Record

```
BEGIN
   UPDATE employees
   SET salary = v_emp.salary
   WHERE employee_id = v_emp.emp_id;
END;
```

4. DELETE Using a Record

```
BEGIN
   DELETE FROM employees
   WHERE employee_id = v_emp.emp_id;
END;
```

### What are COLLECTIONS?

In PL/SQL, collections are composite data types that allow to store and manipulate multiple values (elements) as a single unit, similar to arrays or lists in other programming languages.
Collections are useful for handling sets of data in memory.

There are three main types of collections in PL/SQL:

1. Associative Arrays (Index-by Tables):
   - Key-value pairs, where the key can be an integer or string
   - Size is dynamic and can be sparse
   ```
   TYPE num_table IS TABLE OF NUMBER INDEX BY PLS_INTEGER;
   v_nums num_table;
   v_nums(1) := 100;
   v_num2(2) := 200;
   ```
2. Nested Tables:
   - Like arrays, but can be stored in database columns and can be sparse
   - Can be extended dynamically
   ```
   TYPE num_table IS TABLE OF NUMBER;
   v_nums num_table := num_table(10,20,30);
   ```
3. VARRAYs(Variable-size Arrays):
   - Arrays with a fixed maximum size.
   2. Elements are always stored in order and densely packed
   ```
   TYPE num_varray IS VARRAY(5) OF NUMBER;
   v_nums num_varray := num_varray(1,2,3);
   ```

### VARRAYs

VARRAYs (Variable-size Arrays) in PL/SQL.

A VARRAY (variable-size array) is a type of collection in PL/SQL that can store a fixed number of elements of the same data type. VARRAYs are always dense (no gaps between elements) and maintain the order of insertion.

- Fixed maximum size defined at creation
- Elements are always stored in order and densely packed
- Can be used as PL/SQL variables, parameters or columns in tables

```
DECLARE
   TYPE num_varray IS VARRAY(5) OF NUMBER;
   v_nums num_varray := num_varray(10,20,30);
BEGIN
   FOR i IN 1..v_nums.count() LOOP
      DBMS_OUTPUT.PUT_LINE('Element: ' || i || ': ' || v_nums(i));
   END LOOP;

   FOR i IN v_nums.first()..v_nums.last() LOOP
      DBMS_OUTPUT.PUT_LINE(v_nums(i));
   END LOOP;

   DBMS_OUTPUT.PUT_LINE(v_nums.limit());
END;
```

- Use VARRAYs when know the maximum number of elements in advance.
- Suitable for small, ordered collections where the size does not change frequently.
- Drop a type: `DROP TYPE type_name`

### Nested Tables

A nested table is a type of collection in PL/SQL that can store an arbitrary number of elements, similar to a one-dimensional array, but with more flexibility. Nested tables can be sparse and can be stored in database columns.

- Can grow dynamically
- Can be sparse
- Can be used as PL/SQL variables, parameters, or columns in tables.

```
DECLARE
   TYPE num_table IS TABLE OF NUMBER;
   v_nums num_table := num_table(10,20,30,40);
BEGIN
   -- Accessing Elements
   FOR i IN 1..v_nums.count() LOOP
      DBMS_OUTPUT.PUT_LINE('Element: ' || i || ': ' || v_nums(i));
   END LOOP;

   -- Deleting an element
   v_nums.DELETE(2);
END;
```

- Use nested tables when need a collection that can grow or shrink dynamically
- Suitable for storing and manipulating sets of data in memory or as columns in database tables.

### Associative Arrays (Index-by Tables)

An associative array is a collection type in PL/SQL that stores key-value pairs, where the key can be an integer or a string. Associative arrays are dynamic and can be sparse, making them very flexible for in-memory lookups and temporary storage.

- Keys can be integers or strings
- Size is dynamic
- Can be sparse
- Only exist in memory

```
DECLARE
   TYPE num_table IS TABLE OF NUMBER INDEX BY PLS_INTEGER;
   v_nums num_table;
BEGIN
   v_nums(1) := 100;
   v_nums(2) := 200;
   v_nums(3) := 300;

   FOR i IN 1..10 LOOP
      IF v_nums.EXISTS(i) THEN
         DBMS_OUTPUT.PUT_LINE(v_nums(i));
   END LOOP;
END;
```

```
DECLARE
   TYPE name_table IS TABLE OF NUMBER INDEX BY VARCHAR2(20);
   v_ages name_table;
BEGIN
   v_ages('Alice') := 30;
   v_ages('Bob') := 25;

   DBMS_OUTPUT.PUT_LINE('Alice age: ' || v_ages('Alice'));
   DBMS_OUTPUT.PUT_LINE('Bob age: ' || v_ages('Bob'));
END;
```

- Use associative arrays for fast, flexible in-memory lookups.
- Ideal for temporary data storage and manipulation within PL/SQL blocks and procedures.

### Storing Collections in Tables

In Oracle, can store collections (specially nested tables and varrays) as columns in database tables. This allows to associate a set of values with a single row, similar to storing an arrays or list inside a table cell.

Steps to store collections in Tables:

1. Define a Collection Type at the Schema Level:

```
CREATE OR REPLACE TYPE num_array IS VARRAY(5) OF NUMBER;
CREATE OR REPLACE TYPE num_table IS TABLE OF NUMBER;
```

2. Create a Table with a collection column:

```
CREATE TABLE dept_projects(
   dept_id NUMBER,
   project_ids num_varray
);
CREATE TABLE student_marks(
   student_id NUMBER,
   marks num_table
);
```

3. Insert Data into the Table:

```
INSERT INTO dept_projects VALUES(10, num_array(101,102,103));
INSERT INTO student_marks VALUES(1, num_table(80,50,90));
```

4. Select Data from the Table:

```
SELECT * FROM dept_projects;
SELECT * FROM student_marks;
```

5. Access Collection Elements:

```
DECLARE
   v_marks num_table;
BEGIN
   SELECT marks INTO v_marks FROM student_marks WHERE student_id = 1;
   FOR i IN 1..v_marks.COUNT LOOP
      DBMS_OUTPUT.PUT_LINE('Mark: ' || v_marks(i));
   END LOOP;
END;
```

- Associate arrays can't be stored in table columns, only nested tables and varrays can
- Collections stored in tables are useful for modeling one-to-many relationship within a single row.
