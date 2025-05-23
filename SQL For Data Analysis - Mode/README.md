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

### SQL HAVING
```
SELECT year, month, MAX(high) AS month_high
FROM tutorial.aapl_historical_stock_price
GROUP BY year, month
HAVING MAX(high) > 400
ORDER BY year, month;
```

`HAVING` is the clean way to filter a query that has been aggregated.

### Query Clause Order
1. SELECT
2. FROM
3. WHERE
4. GROUP BY
5. HAVING
6. ORDER BY

### SQL CASE
The `CASE` statement is SQL's way of handling if/then login. The `CASE` statement is followed by at least one pair of `WHEN` and `THEN` statements. Every `CASE` statement must end with the `END` statement. The `ELSE` statement is optional and provides a way to capture values not specified in the `WHEN`/`THEN` statements. 

```
SELECT player_name, 
        year,
        CASE WHEN year='SR' THEN 'yes' ELSE 'no' END AS is_a_senior
FROM benn.college_football_players;
```

Adding multiple conditions to a CASE statement.
```
SELECT player_name,
    weight,
    CASE WHEN weight > 250 THEN 'over 250'
        WHEN weight > 200 AND weight <= 250 THEN '201-250'
        WHEN weight > 175 AND weight <= 200 THEN '176-200'
        ELSE '175 or under' END AS weight_group
FROM benn.college_football_players;
```

```
SELECT player_name,
    CASE WHEN year='FR' AND position='WR' THEN 'frosh_wr' ELSE NULL END AS sample_case_statement
FROM benn.college_football_players;
```

```
SELECT CASE WHEN year = 'FR' THEN 'FR'
    ELSE 'Not FR' END AS year_group,
    COUNT(1) AS count
FROM benn.college_football_players
GROUP BY CASE WHEN year='FR' THEN 'FR' 
ELSE 'Not FR' END;
```

```
SELECT CASE WHEN year='FR' THEN 'FR'
    WHEN year='SO' THEN 'SO'
    WHEN year='JR' THEN 'JO'
    WHEN year='SR' THEN 'SR'
    ELSE 'No Year Data' END AS year_group,
    COUNT(1) AS count
FROM benn.college_football_players
GROUP BY 1;
```

```
SELECT COUNT(CASE WHEN year='FR' THEN 1 ELSE NULL END) AS fr_count,
COUNT(CASE WHEN year='SO' THEN 1 ELSE NULL END) AS so_count
FROM benn.college_football_players;
```

### SQL DISTINCT
Returns the unique values in a particular column using `SELECT DISTINCT` syntax.
```
SELECT DISTINCT month
FROM tutorial.aapl_historical_stocK_price;
```
If includes two or more columns in a `SELECT DISTINCT` clause, results will contain all of the unique pairs of those columns.
```
SELECT DISTINCT year, month
FROM tutorial.aapl_historical_stock_price;
```

```
SELECT COUNT(DISTINCT months) AS unique_months
FROM tutorial.aapl_historical_stock_price;
```

It's worth nothing that using `DISTINCT`, particularly in aggregations, can slow queries down quite a bit.

### SQL Joins
Anatomy of a join:
```
SELECT teams.conference AS conference,
    AVG(players.weight) AS average_weight
FROM benn.college_football_players players
JOIN benn.college_football_teams teams
ON teams.school_name = players.school_name
GROUP BY teams.conference
ORDER BY AVG(players.weight) DESC;
```

Aliases in SQL: When performing joins, it's easiest to give table names aliases, like `benn.college_football_players players`.

JOIN and ON: `ON` indicates how the two tables relate to each other. `ON teams.school_name = players.school_name`

```
SELECT *
FROM benn.college_football_players players
JOIN benn.college_school_teams teams
ON teams.school_name = players.school_name;
```

### SQL INNER JOIN
Inner join can be written as either `JOIN ... ON` or `INNER JOIN ... ON`. Inner joins eliminate rows from both tables that do not satisfy the join condition set forth in the `ON` statement. In mathematical terms, an inner join is the intersection of the two tables.
<img src='../images/4.png' alt='Inner Join' />
Therefore, if a player goes to a school that isn't in the teams, that player won't be included in the result from an inner join. Similarly, if there are schools in the teams table that don't match to any schools in the players table, those rows won't be included in the results either.

Joining tables with identical column names:

```
SELECT players.*,
    teams.*
FROM benn.college_football_players players
JOIN benn.college_football_teams teams
ON teams.school_name = players.school_name;
```

### SQL Outer Joins
Outer joins are joins that return matched values and unmatched values from either or both tables. There are a few types of outer joins:
* `LEFT JOIN`: returns only unmatched rows from the left tabel, as well as matched rows in both tables.
* `RIGHT JOIN`: returns only unmatched rows from the right table, as well as matched rows in both tables.
* `FULL OUTER JOIN`: returns unmatched rows from both tables, as well as matched rows in both tables.

`LEFT JOIN` is also referred to as `OUTER LEFT JOIN`. `RIGHT JOIN` is also referred to as `OUTER RIGHT JOIN`. `FULL OUTER JOIN` is also referred to as `OUTER JOIN`.

Outer Joins vs. Inner join: When performing an inner join, rows from wither table that are unmatched in the other table are not returned. In an outer join, unmatched rows in one or both tables can be returned.
```
SELECT users.name, likes.like FROM users
JOIN likes 
ON users.id = likes.user_id;
```

<img src='../images/5.png' alt='Inner Join' />

### SQL LEFT JOIN

```
SELECT companies.permalink AS companies_permalink, companies.name AS companies_name, acquisitions.company_permalink AS acquisitions_permalink,
acquisitions.acquired_at AS acquired_date
FROM tutorial.crunchbase_companies companies
LEFT JOIN tutorial.crunchbase_acquisition acquisitions
ON companies.permalink=acquisitions.company_permalink;
```

### SQL RIGHT JOIN
Right joins return all rows from the table in the `RIGHT JOIN` clause and only matching rows from the table in the `FROM` clause.
`RIGHT JOIN` is rarely used because it can achieve the results of a `RIGHT JOIN` by simply switching the two tables names in a `LEFT JOIN`.
Same results for LEFT JOIN & RIGHT JOIN (Produces the same result):
```
SELECT companies.permalink AS companies_permalink, companies.name AS companies_name, acquisitions.company_permalink AS acquisitions_permalink, acquisitions.acquired_at AS acquired_date
FROM tutorial.crunchbase_acquisitions acquisitions
RIGHT JOIN tutorial.crunchbase_companies companies
ON companies.permalink = acquisitions.company_permalink;

SELECT companies.permalink AS companies_permalink, companies.name AS companies_name, acquisitions.company_permalink AS acquisitions_permalink, acquisitions.acquired_at AS acquired_date
FROM tutorial.crunchbase_companies companies
LEFT JOIN tutorial.crunchbase_acquisitions acquisitions
ON companies.permalink = acquisitions.company_permalink;
```

`LEFT JOIN` & `RIGHT JOIN` can be written as `LEFT OUTER JOIN` & `RIGHT OUTER JOIN` respectively.

### SQL Joins Using WHERE or ON
Filtering in the ON clause: Normally filtering is processed in the `WHERE` clause once the two tables have already been joined. It's possible to filter one or both of the tables before joining them. 
```
SELECT companies.permalink AS companies_permalink, companies.name AS companies_name, acquisitions.company_permalink AS acquisitions_permalink, acquisitions.acquired_at AS acquired_date
FROM tutorial.crunchbase_companies companies
LEFT JOIN tutorial.crunchbase_acquisitions acquisitions
ON companies.permalink = acquisitions.company_permalink
AND acquisitions.company_permalink != '/company/1000memories'
ORDER BY 1;
```
Above query returns everything in the `tutorial.crunchbase_acquisitions` table was joined on except for the row for which company_permalink is '/company/1000memories'. The conditional statement `AND ...` is evaluated before the join occurs. 

Filtering in the WHERE clause: If move the same filter to the `WHERE` clause, will notice that the filter happens after the tables are joined. The result is that the 1000memories row is joined onto the original table, but then it is filtered our entirely(in both tables) in the `WHERE` clause before displaying results.
```
SELECT companies.permalink AS companies_permalink, companies.name AS companies_name, acquisitions.company_permalink AS acquisitions_permalink, acquisitions.acquired_at AS acquired_date
FROM tutorial.crunchbase_acquisitions acquisitions
LEFT JOIN tutorial.crunchbase_acquisitions acquisitions
ON companies.permalink = acquisitions.company_permalink
WHERE acquisitions.company_permalink != '/company/1000memories'
OR acquisitions.company_permalink IS NULL
ORDER BY 1;
```

### SQL FULL OUTER JOIN
`FULL JOIN`, which can also be written as `FULL OUTER JOIN`. `FULL JOIN` returns unmatched rows from both tables. It is commonly used in conjunction with aggregations to understand the amount of overlap between two tables.

```
SELECT COUNT(CASE WHEN companies.permalink IS NOT NULL AND acquisitions.company_permalink IS NULL THEN companies.permalink ELSE NULL END) AS companies_only,
COUNT(CASE WHEN companies.permalink IS NOT NULL AND acquisitions.company_permalink IS NOT NULL THEN companies.permalink ELSE NULL END) AS both_tables,
COUNT(CASE WHEN companies.permalink IS NULL AND acquisitions.company_permalink IS NOT NULL THEN acquisitions.company_permalink ELSE NULL END) AS acquisitions_only
FROM tutorial.crunchbase_companies companies
FULL JOIN tutorial.crunchbase_acquisitions acquisitions
ON companies.permalink = acquisitions.company_permalink;
```

### SQL UNION
SQL joins allow to combine two datasets side-by-side, but `UNION` allows to stack one dataset on top of the other. Differently, `UNION` allows to write two select statements, and to have the results of one statement display in the same table as the results from the other statement.
The following query will display all results from the first portion of the query, then all results from the second portion in the same table.
```
SELECT * FROM tutorial.crunchbase_investments_part1
UNION
SELECT * FROM tutorial.crunchbase_investments_part2;
```

Note that, `UNION` only appends distinct values. More specifically, when use `UNION`, the dataset is appended, and any rows in the appended table are exactly identical to rows in the first table are dropped. If like to append all the values from the second table, use `UNION ALL`. 
```
SELECT * FROM tutorial.crunchbase_investments_part1
UNION ALL
SELECT * FROM tutorial.crunchbase_investments_part2;
```

SQL has strict rules for appending data:
* Both tables must have the same number of columns.
* The columns must have the same data types in the same order as the first table.

### SQL Joins with Comparison Operators
```
SELECT companies.permalink, companies.name, companies.status, COUNT(investments.investor_permalink) AS investors
FROM tutorial.crunchbase_companies companies
LEFT JOIN tutorial.crunchbase_investments_part1 investments
ON companies.permalink = investments.company_permalink
AND investments.funded_year > companies.founded_year + 5
GROUP BY 1,2,3;
```

```
SELECT companies.permalink, companies.name, companies.status, COUNT(investments.investor_permalink) AS investors
FROM tutorial.crunchbase_companies companies
LEFT JOIN tutorial.crunchbase_investments_part1 investments
ON companies.permalink = investments.company_permalink
WHERE investments.funded_year > companies.founded_year + 5
GROUP BY 1,2,3;
```

### SQL Joins on Multiple Keys
Reasons to join tables on multiple foreign keys:
* To do with accuracy
* To do with performance. SQL uses "indexes" (essentially pre-defined joins) to speed up queries.

```
SELECT companies.permalink, companies.name, investments.company_name, investments.company_permalink
FROM tutorial.crunchbase_companies companies
LEFT JOIN tutorial.crunchbase_investments_part1 investments
ON companies.permalink = investments.company_permalink
AND companies.name = investments.company_name;
```

### SQL Self Joins
Self joining means joining a table to itself.
```
SELECT DISTINCT japan_investments.company_name, japan_investments.company_permalink
FROM tutorial.crunchbase_investments_part1 japan_investments
JOIN tutorial.crunchbase_investments_part1 gb_investments
ON japan_investments.company_name = gp_investments.company_name
AND gb_investments.investor_country_code = "GBR"
WHERE japan_investments.investor_country_code = 'JPN'
ORDER BY 1;
```

### SQL Data Types
`COUNT` works with any data type, but `SUM` only works for numerical data. In order to use `SUM`, the data must appear to be numeric, but it must also be stored in the database in a numeric form.

The `INTEGER` data type only stores whole numbers - no decimals. The `DOUBLE PRECISION` data type, on the other hand can store between 15 and 17 significant decimal digits.

Some SQL Data Types: CHAR, VARCHAR, BINARY, BLOB, MEDIUMBLOB, LONGBLOB, ENUM, SET, BOOL, BOOLEAN, INT, INTEGER, FLOAT, DOUBLE, DOUBLE PRECISION, DECIMAL, DATE, DATETIME, TIMESTAMP, TIME, YEAR, etc.

### Data Wrangling with SQL
Data munging or data wrangling is loosely the process of manually converting or mapping data from one row form into another format that allows for more convenient consumption of the data with the help of semi-automated tools.
In other words, data wrangling or munging is the process of programmatically transforming data into a format that makes it easier to work with. This might mean modifying all of the values in a given column in a certain way or merging multiple columns together. The necessity for data wrangling is often a biproduct of poorly collected or presented data.

### Using SQL String Functions to Clean Data

##### Cleaning strings (LEFT, RIGHT, TRIM)
* Cleaning Strings: Let's start with `LEFT`. `LEFT` is used to pull a certain number of characters from the left side of a string and present them as a separate string. The syntax is `LEFT(string, number of characters)`.

```
SELECT incidnt_num, date, LEFT(date, 10) AS cleaned_date
FROM tutorial.sf_crime_incidents_2014_01;
```

`RIGHT` does the same thing, but from the right side.
```
SELECT date, RIGHT(date, 17) AS cleaned_time
FROM tutorial.sf_crime_incidents_2014_01;
```

`LENGTH` function returns the length of a string.
When using functions within other functions, it's important to remember that the innermost functions will be evaluated first, followed by the functions that encapsulated them.

The `TRIM` function is used to remove characters from the beginning and end of a string.
```
SELECT location, TRIM(both '()' FROM location)
FROM tutorial.sf_crime_incidents_2014_01;
```
The `TRIM` function takes 3 arguments. First, have to specify whether want to remove characters from the beginning('leading'), the end('trailing') or both('both', as used above). Next must specify all characters to be trimmed. Any characters included in the single quotes will be removed from both beginning, end or both sides of the string. Finally, must specify the text want to trim using `FROM`.

##### POSITION and STRPOS

`POSITION` allow to specify a substring, then returns a numerical value equal to the character number(counting from left) where that substring first appears in the target string.
```
SELECT incidnt_num, descript, POSITION('A' IN descript) AS a_position
FROM tutorial.sf_crime_incidents_2014_01;
```

Can also able to use the `STRPOS` function to achieve the same results - just replace `IN` with a comma and switch the order of the string and substring.
```
SELECT incidnt_num, descript, STRPOS(descript, 'A') AS a_position
FROM tutorial.sf_crime_incidents_2014_01;
```

##### SUBSTR
`SUBSTR` function syntax: `SUBSTR(*string, *startingg character position*, *# of characters*)`.
```
SELECT incidnt_num, date, SUBSTR(date, 4, 2) AS day
FROM tutorial.sf_crime_incidents_2014_01;
```

##### CONCAT
Combine strings using `CONCAT`.
```
SELECT CONCAT(day_of_week, ', ', LEFT(date, 10)) AS day_and_date
FROM tutorial.sf_crime_incidents_2014_01;
```

Alternatively, can use two pipe characters (`||`) to perform the same concatenation.
```
SELECT day_of_week || ', ' || LEFT(date, 10) AS day_and_date
FROM tutorial.sf_crime_incidents_2014_01;
```

##### Changing case with UPPER and LOWER
`LOWER` to force every character in a string to become lower-case. `UPPER` to make all the letters appear in upper-case.
```
SELECT UPPER(address) AS address_upper, LOWER(address) AS address_lower
FROM tutorial.sf_crime_incidents_2014_01;
```

##### Turning strings into dates
```
SELECT incidnt_num, date, (SUBSTR(date, 7, 4) || '-' || LEFT(date, 2) || '-' || SUBSTR(date, 4, 2))::date AS cleaned_date
FROM tutorial.sf_crime_incidents_2014_01;
```

##### Turning dates into more useful dates
```
SELECT cleaned_date,
    EXTRACT('year' FROM cleaned_date) AS year,
    EXTRACT('month' FROM cleaned_date) AS month,
    EXTRACT('day' FROM cleaned_date) AS day,
    EXTRACT('hour' FROM cleaned_date) AS hour,
    EXTRACT('minute' FROM cleaned_date)
    AS minute
FROM tutorial.sf_crime_incidents_cleandate;
```

The `DATE_TRUNC` function rounds a date to whatever precision is specified. The value displayed is the first value in that period.
```
SELECT cleaned_date,
    DATE_TRUNC('year', cleaned_date) AS year,
    DATE_TRUNC('month', cleaned_date) AS month
FROM tutorial.sf_crime_incidents_cleandate;
```

##### COALESCE
`COALESCE` is used to replace the null values.
```
SELECT descript, COALESCE(descript, 'No Description')
FROM tutorial.sf_crime_incidents_clean_date
ORDER BY descript DESC;
```

### Writing Subqueries in SQL
Subqueries (also known as inner queries or nested queries) are a tool for performing operations in multiple steps.
```
SELECT sub.* 
FROM (SELECT * FROM tutorial.sf_crime_incidents_2014_01 WHERE day_of_week = 'FRIDAY') sub
WHERE sub.resolution = 'NONE'; 
```
Inner query must actually run on its own, as the database will treat it as an independent query. Once the inner query runs, the outer query will run using the results from the inner query as its underlying table. Subqueries are required to have names, which are added after parentheses.

Using subqueries to aggregate in multiple stages:
```
SELECT LEFT(sub.date, 2) AS cleaned_month,
    sub.day_of_week,
    AVG(sub.incidents) AS average_incidents
FROM (SELECT day_of_week, date, COUNT(incident_num) AS incidents FROM tutorial.sf_crime_incidents_2014_01 GROUP BY 1,2) sub
GROUP BY 1,2
ORDER BY 1,2;
```
In general, it's easiest to write inner queries first and revise them until the results make sense.

Subqueries in conditional logic:
Subqueries can be used in conditional logic (in conjunction with WHERE, JOIN/ON, CASE). The following query returns all of the entries from the earliest date in the dataset.
```
SELECT *
FROM tutorial.sf_crime_incidents_2014_01
WHERE Date = (SELECT MIN(date) FROM tutorial.sf_crime_incidents_2014_01);
```

`IN` is the only type of conditional logic that will work when the inner query contains multiple results.
```
SELECT *
FROM tutorial.sf_crime_incidents_2014_01
WHERE DATE IN (SELECT date FROM tutorial.sf_crime_incidents_2014_01 ORDER BY date LIMIT 5);
```

Joining subqueries:
```
SELECT *
FROM tutorial.sf_crime_incidents_2014_01 incidents
JOIN (SELECT date FROM tutorial.sf_crime_incidents_2014_01 ORDER BY date LIMIT 5) sub
ON incidents.date = sub.date;
```

```
SELECT incidents.*, sub.incidents AS incidents_that_day
FROM tutorial.sf_crime_incidents_2014_01 incidents
JOIN (SELECT date, COUNT(incident_num) AS incidents FROM tutorial.sf_crime_incidents_2014_01 ORDER BY 1) sub
ON incidents.date = sub.date
ORDER BY sub.incidents DESC, time;
```

```
SELECT COALESCE(acquisitions.month, investments.month) AS month,
       acquisitions.companies_acquired,
       investments.companies_rec_investment
  FROM (
        SELECT acquired_month AS month,
               COUNT(DISTINCT company_permalink) AS companies_acquired
          FROM tutorial.crunchbase_acquisitions
         GROUP BY 1
       ) acquisitions

  FULL JOIN (
        SELECT funded_month AS month,
               COUNT(DISTINCT company_permalink) AS companies_rec_investment
          FROM tutorial.crunchbase_investments
         GROUP BY 1
       )investments

    ON acquisitions.month = investments.month
 ORDER BY 1 DESC
```

Subqueries and UNIONS:

```
SELECT COUNT(*) AS total_rows
FROM (
    SELECT * FROM tutorial.crunchbase_investments_part1
    UNION ALL
    SELECT * FROM tutorial.crunchbase_investments_part2
) sub;
```

### SQL Window Functions
A window function performs a calculation across a set of table rows that are somehow related to the current row. This is comparable to the type of calculation that can be done with an aggregate function. But unlike regular aggregate functions, use of a window function does not cause rows to become grouped into a single output row — the rows retain their separate identities. Behind the scenes, the window function is able to access more than just the current row of the query result.

```
SELECT duration_seconds,
SUM(duration_seconds) OVER (ORDER BY start_time) AS running_total
FROM tutorial.dc_bikeshare_q1_2012
```
Adding OVER designates SUM() as a Window Function, means "Take the sum of duration_seconds over the entire result set, in order by start_time"

If want to narrow the window from the entire dataset to individual groups within the dataset, can be used PARTITION BY to do so:
```
SELECT start_terminal, duration_seconds, SUM(duration_seconds) OVER (PARTITION BY start_terminal ORDER BY start_time) AS running_total
FROM tutorial.dc_bikeshare_q1_2012
WHERE start_time < '2012-01-08'
```

The usual suspects: SUM, COUNT, and AVG:
```
SELECT start_terminal,
       duration_seconds,
       SUM(duration_seconds) OVER
         (PARTITION BY start_terminal) AS running_total,
       COUNT(duration_seconds) OVER
         (PARTITION BY start_terminal) AS running_count,
       AVG(duration_seconds) OVER
         (PARTITION BY start_terminal) AS running_avg
  FROM tutorial.dc_bikeshare_q1_2012
 WHERE start_time < '2012-01-08'
```

Alternatively, the same functions with ORDER BY:
```
SELECT start_terminal,
       duration_seconds,
       SUM(duration_seconds) OVER
         (PARTITION BY start_terminal ORDER BY start_time)
         AS running_total,
       COUNT(duration_seconds) OVER
         (PARTITION BY start_terminal ORDER BY start_time)
         AS running_count,
       AVG(duration_seconds) OVER
         (PARTITION BY start_terminal ORDER BY start_time)
         AS running_avg
  FROM tutorial.dc_bikeshare_q1_2012
 WHERE start_time < '2012-01-08'
```

### Performance Tuning SQL Queries
SQL Performance Tuning: SQL tuning is the process of improving SQL queries to accelerate servers performance. It's general purpose is to reduce the amount of time it takes a user to receive a result after issuing a query, and to reduce the amount of resources used to process a query.

The theory behind query run time:
A database is a piece of software that runs on a computer, and is subject to the same limitations as all software - it can only process as much information as its hardware is capable of handling. The way to make a query run faster is to reduce the number of calculations that the software (and therefore hardware) must perform.
Let's address some of the high-level things that will affect the number of calculations need to make and therefore querys runtime:

* Table size: If query hits one or more tables with millions of rows or more, it could affect performance.
* Joins: If query joins two tables in a way that substantially increases the row count of the result set, query is likely to be slow.
* Aggregations: Combining multiple rows to produce a result requires more computation than simply retrieving those rows.

Query runtime is also dependent on some things that can't really control related to the database itself:

* Other users running queries: The more queries running concurrently on a database, the more the database must process at a given time and the slower everything will run. It can be especially bad if others are running particularly resource-intensive queries that fulfill some of the above criteria.
* Database software and optimization: This is something probably can't control, but if know the system is using, can work within its bounds to make queries more efficient.

Reducing Table Size:
```
SELECT *
  FROM benn.sample_event_table
 WHERE event_date >= '2014-03-01'
   AND event_date <  '2014-04-01'
```

```
SELECT COUNT(*)
  FROM benn.sample_event_table
 LIMIT 100
```

Making Joins Less Complicated:
```
SELECT teams.conference AS conference,
       players.school_name,
       COUNT(1) AS players
  FROM benn.college_football_players players
  JOIN benn.college_football_teams teams
    ON teams.school_name = players.school_name
 GROUP BY 1,2
```