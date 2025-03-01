### SQL
SQL (Structured Query Language) is a programming language designed for managing data in a relational database. It's been around since the 1970s and is the most common method of accessing data in database. SQL has a variety of functions that allow its users to read, manipulate and change data.

### Database
A database is an organized collection of data.

### SQL SELECT
`SELECT` indicates which columns you'd like to view, and `FROM` identifies the table that they live in.

```
SELECT year, month, west FROM tutorial.us_housing_units;
```
The query is telling the database to return the `year`, `month`, and `west` columns from the table `tutorial.us_housing_units`.
If wants to select every column in a table, you can use `*` instead of the column names.
```
SELECT * FROM tutorial.us_housing_units;
```

### Column Names
```
SELECT west as "West Region", south AS "South Region" FROM tutorial.us_housing_units;
```

### SQL LIMIT command
```
SELECT * FROM tutorial.us_housing_units LIMIT 100;
```

### SQL WHERE
Filtering data using `WHERE` clause.
```
SELECT * FROM tutorial.us_housing_units WHERE month=1;
```
The results will only include rows where the `month` column contains the value `1`.
