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

### SQL Comparison Operators
Comparison operators on numerical data: The most basic way to filter data using comparison operators. 
Equal to (=), Not equal to (<> or !=), Greater than (>), Less than (<), Greater than or equal to (>=), Less than or equal to (<=).
```
SELECT * FROM tutorial.us_housing_units WHERE west > 90;

SELECT * FROM tutorial.us_housing_units WHERE month_name != 'January';
```

Arithmetic in SQL: Arithmetic in SQL using the `+`, `-`, `*`, `/` operators.

```
SELECT year, month, west, south, west + south - 4 * year AS nonsense_column
FROM tutorial.us_housing_units;

SELECT year, (west + south)/2 AS south_west_avg
FROM tutorial.us_housing_units;
```

### SQL Logical Operators
Logical operators allow to use multiple comparison operators in one query.
* `LIKE` - allows to match similar values, instead of exact values.
* `IN` - allows to specify a list of values you'd like to include.
* `BETWEEN` - allows to select only rows within a certain range
* `IS NULL` - allows to select rows that contain no data in a given column
* `AND` - allows to select only rows that satisfy two conditions
* `OR` - allows to select rows that satisfy either of two conditions.
* `NOT` - allows to select rows that do not match a certain condition

### SQL LIKE
`LIKE` is a logical operator in SQL that allows to match on similar values rather than exact ones.
```
SELECT * FROM tutorial.billboard_top_100_year_end
WHERE group_name LIKE 'Snoop%';
```

`%` is referred to as a "Wildcard". `LIKE` is case-sensitive, meaning that the above query will only capture matches that start with a capital "S" and lower-case "noop". To ignore case when you're matching values, can use the `ILIKE` command.
```
SELECT * FROM tutorial.billboard_top_100_year_end
WHERE group_name ILIKE 'snoop%';
```

Use `_` (a single underscore) to substitute for an individual character
```
SELECT * FROM tutorial.billboard_top_100_year_end
WHERE artist ILIKE 'dr_ke';
```

### SQL IN
`IN` is a Logical operator in SQL that allows you to specify a list of values that you'd like to include in the results. 

```
SELECT * FROM tutorial.billboard_top_100_year_end
WHERE year_rank IN (1,2,3);

SELECT * FROM tutorial.billboard_top_100_end
WHERE artist IN ('Taylor Swift', 'Usher', 'Ludacris');
```

### SQL BETWEEN
`BETWEEN` is a logical operator in SQL that allows to select only rows that are within a specific range. It has to be paired with the `AND` operator.
```
SELECT * FROM tutorial.billboard_top_100_year_end
WHERE year_rank BETWEEN 5 AND 10;
```

### SQL IS NULL
`IS NULL` is a logical operator in SQL that allows to exclude rows with missing data from results. Some tables contain null values - cells with no data in them at all. Select rows that contain no data in a given column by using `IS NULL`.

```
SELECT * FROM tutorial.billboard_top_100_year_end
WHERE artist IS NULL;
```

### SQL AND
`AND` is a logical operator in SQL that allows to select rows that satisfy two conditions. 
```
SELECT * FROM tutorial.billboard_top_100_year_end
WHERE year = 2022 AND year_rank <= 10;

SELECT * FROM tutorial.billboard_top_10_year_end
WHERE year = 2022 AND year_rank <= 10 AND group_name ILIKE '%feat%';
```

### SQL OR
`OR` is a logical operator in SQL that allows to select rows that satisfy either of two conditions.
```
SELECT * FROM tutorial.billboard_top_100_year_end
WHERE year_rank = 5 OR artist = 'Gotye';
```

Combine AND with OR using parenthesis.
```
SELECT * FROM tutorial.billboard_top_100_year_end
WHERE year = 2013 
AND (group_name ILIKE '%macklemore%' OR group_name ILIKE '%timberlake%');
```

### SQL NOT
`NOT` is a logical operator in SQL that can put before any conditional statement to select rows for which that statement is false.

```
SELECT * FROM tutorial.billboard_top_100_year_end
WHERE year=2013 AND year_rank NOT BETWEEN 2 AND 3;
```

### SQL ORDER BY
The `ORDER BY` clause allows to record results based on the data in one or more columns. 

```
SELECT * FROM tutorial.billboard_top_100_year_end
ORDER BY artist;

SELECT * FROM tutorial.billboard_top_100_year_end
WHERE year = 2013
ORDER BY year_rank;

SELECT * FROM tutorial.billboard_top_100_year_end 
WHERE year = 2013
ORDER BY year_rank DESC;

SELECT * FROM tutorial.billboard_top_100_year_end
WHERE year_rank <= 3
ORDER BY year DESC, year_rank;
```

### Comments in SQL
-- Single line comment

/*
Multi-line
Comment
*/

### SQL Aggregate Functions
* `COUNT` - counts how many rows are in a particular column
* `SUM` - adds together all the values in a particular column
* `MIN` and `MAX` - return the lowest and highest values in a particular column, respectively.
* `AVG` - calculates the average of a group of selected values

### SQL Count
`COUNT` is a SQL aggregate function for counting the number of rows in a particular column.

```
SELECT COUNT(*) FROM tutorial.aapl_historical_stock_price;

SELECT COUNT(high) 
FROM tutorial.aapl_historical_stock_price;

SELECT COUNT(date) AS count_of_date
FROM tutorial.aapl_historical_stock_price;

SELECT COUNT(date) AS "Count of Date"
FROM tutorial.aapl_historical_stock_price;
```

`COUNT(1)` has the same effect as `COUNT(*)`.

### SQL SUM
`SUM` is a SQL aggregate function that totals the values in a given column. Unlike `COUNT`, `SUM` can only use on columns containing numerical values.

```
SELECT SUM(volume) 
FROM tutorial.aapl_historical_stock_price;
```

### SQL MIN/MAX
`MIN` & `MAX` are SQL aggregation functions that return the lowest and highest values in a particular column.

```
SELECT MIN(volume) AS min_volume, MAX(volume) AS max_volume
FROM tutorial.aapl_historical_stock_price;
```

### SQL AVG
`AVG` is a SQL aggregate function that calculates the average of a selected group of values. It can only be used on numerical columns and ignores nulls completely.

```
SELECT AVG(high)
FROM tutorial.aapl_historical_stock_price
WHERE high IS NOT NULL;
```

### SQL GROUP BY
`GROUP BY` allows to separate data into groups, which can be aggregated independently of one another.

```
SELECT year, COUNT(*) AS count 
FROM tutorial.aapl_historical_stock_price
GROUP BY year;

SELECT year, month, COUNT(*) AS count
FROM tutorial.aapl_historical_stock_price
GROUP BY year, month;
```

GROUP BY column numbers:
```
SELECT year, month, COUNT(*) AS count
FROM tutorial.aapl_historical_stock_price
GROUP BY 1,2;
```

Using GROUP BY with ORDER BY:
```
SELECT year, month, COUNT(*) AS count
FROM tutorial.aapl_historical_stock_price
GROUP BY year, month
ORDER BY month, year;
```