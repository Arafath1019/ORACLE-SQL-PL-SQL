## ORACLE PL/SQL

#### Topics
* Introduction to PL/SQL
* PL/SQL Variables
* Manipulate Data
* IF Statement
* CASE Statement
* LOOP Statement
* Composite Data Types
* Cursors
* Exceptions
* Procedures
* Functions
* Packages
* Using Dynamic SQL
* Triggers
* Managing Dependencies


#### Introduction to PL/SQL

##### Benefits of PL/SQL
* Integration of procedural constructs with SQL:
The most important advantage of PL/SQL is the integration of procedural constructs with SQL. SQL is a nonprocedural language.
* Improved performance:
Without PL/SQL, you would not be able to logically combine SQL statements as one unit.

##### PL/SQL Block Structure
* DECLARE (optional)
    - Variables, cursors, user-defined exceptions
* BEGIN (mandatory)
    - SQL statements - PL/SQL statements
* EXCEPTION (optional)
    - Actions to perform when exceptions occur
* END; (mandatory)

##### Three types of blocks that make up a PL/SQL program

<img src="../images/3.png" height="auto" width="auto" />

* Anonymous blocks: Anonymous blocks are unnamed blocks. These blocks are not stored in the database.
* Procedures: Procedures are named objects that contain SQL and/or PL/SQL statements.
* Functions: Functions are named objects that contain SQL and/or PL/SQL statements. Unlike a procedure, a function returns a value of a specified data type.

##### Executing an Anonymous Block
```
/*The Below Line Declaration is for DBMS_OUTPUT.PUT_LINE*/
SET SERVEROUTPUT ON

DECLARE
    /* Declarative Section */
    v_fname VARCHAR2(25);
BEGIN
    /* Executable Section */
    SELECT first_name INTO v_fname
    FROM employees WHERE employee_id=200;
    DBMS_OUTPUT.PUT_LINE(' First Name is: ' || v_fname);
END;
/
```

```
SET SERVEROUTPUT ON

DECLARE
    v_myName VARCHAR2(20);
BEGIN
    DBMS_OUTPUT.PUT_LINE('My name is: ' || v_myName);
    v_myName := 'John';
    DBMS_OUTPUT.PUT_LINE('My name is: ' || v_myName);
END;
/
```

```
SET SERVEROUTPUT ON

DECLARE
    v_myName VARCHAR2(20) := 'John';
BEGIN
    v_myName := 'Doe';
    DBMS_OUTPUT.PUT_LINE('My name is: ' || v_myName);
END;
/
```