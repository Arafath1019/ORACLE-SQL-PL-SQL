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

##### Multiple Variable use
```
SET SERVEROUTPUT ON

DECLARE
    V_NAME VARCHAR2(25);
    V_SALARY NUMBER(10);

BEGIN
    SELECT FIRST_NAME, SALARY
    INTO V_NAME, V_SALARY
    FROM EMPLOYEES
    WHERE EMPLOYEE_ID = 200;

    DBMS_OUTPUT.PUT_LINE('FIRST NAME IS: ' || V_NAME);
    DBMS_OUTPUT.PUT_LINE('SALARY IS: ' || V_SALARY);
END;
/
```
##### Avoid using variable names
Declare state variable name and select state variable name should not be same.
```
-- BAD PRACTICE
DECLARE
    FIRST_NAME VARCHAR2(25);
BEGIN
    SELECT FIRST_NAME
    INTO FIRST_NAME
    FROM EMPLOYEE
    WHERE EMPLOYEE_ID=200;
    DBMS_OUTPUT.PUT_LINE('FIRST NAME IS: ' || FIRST_NAME);
END;
/
```
##### %TYPE Attribute
```
DECLARE
    V_FIRST_NAME EMPLOYEES.FIRST_NAME%TYPE;
BEGIN
    SELECT FIRST_NAME
    INTO V_FIRST_NAME
    FROM EMPLOYEES
    WHERE EMPLOYEE_ID=200;
    DBMS_OUTPUT.PUT_LINE('FIRST NAME IS: ' || V_FIRST_NAME);
END;
/
```

```
DECLARE
    V_BALANCE NUMBER(7, 2);
    V_MIN_BALANCE V_BALANCE%TYPE := 1000;
BEGIN
    V_BALANCE := 15000;
    DBMS_OUTPUT.PUT_LINE(V_BALANCE);
END;
/
```
##### Double quotation mark
```
DECLARE
    V_EVENT VARCHAR2(15);
BEGIN
    V_EVENT := q'!Father's Day!';
    DBMS_OUTPUT.PUT_LINE('3rd Sunday in June is: ' || V_EVENT);
    V_EVENT := q'[Mother's Day]';
    DBMS_OUTPUT.PUT_LINE('2nd Sunday in May is: ' || V_EVENT);
END;
/
```

##### Bind Variables
ALso called host variables. Used in SQL statements and PL/SQL blocks. Values can be output using the PRINT command.

```
-- DECLARE Bind Variable
VARIABLE X NUMBER(15);
BEGIN
    :X := 100;
END;
/

-- PRINT Bind Variable value
PRINT X;
```

```
VARIABLE B_EMP_SALARY NUMBER;

BEGIN
    SELECT SALARY
    INTO :B_EMP_SALARY
    FROM EMPLOYEES
    WHERE EMPLOYEE_ID=200;
END;
/

PRINT B_EMP_SALARY
```

```
VARIABLE B_RESULT NUMBER;

BEGIN
    SELECT (SALARY*12)+NVL(COMMISSION_PCT, 0)
    INTO :B_RESULT
    FROM EMPLOYEES
    WHERE EMPLOYEE_ID=200;
END;
/

PRINT B_RESULT
```


##### Commenting the code
```
-- Single Line Comment Example
/* Multi Line
Comment
Example */
```
