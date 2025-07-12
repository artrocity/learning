## SYNTAX

Basic Query Structure

1. SELECT - Retrieves specific columns or data from one or more tables
2. FROM - Specifies which table(s) to retrieve data from
3. WHERE - Filters rows based on specified conditions before grouping
4. ORDER BY - Sorts the result set by one or more columns in ascending or descending order
5. LIMIT / TOP - Restricts the number of rows returned in the result set
6. OFFSET - Adjusts the “place” to start from in the LIMIT

Filtering & Conditions

1. AND - Combines multiple conditions where all must be true
2. OR - Combines multiple conditions where at least one must be true
3. IN - Checks if a value matches any value in a specified list or subquery
4. BETWEEN - Filters values within a specified range (inclusive)
5. LIKE - Searches for patterns in text using wildcards (% and \_)
6. IS NULL / IS NOT NULL - Tests for missing or non-missing values

Grouping & Aggregation

1. GROUP BY - Groups rows with same values and enables aggregate functions
2. HAVING - Filters grouped results after GROUP BY (like WHERE for groups)
3. COUNT() - Returns the number of rows or non-null values
4. SUM() - Calculates the total of numeric values in a column
5. AVG() - Calculates the average of numeric values in a column
6. MAX() / MIN() - Returns the highest or lowest value in a column

Joins & Relationships

1. INNER JOIN - Returns only rows that have matching values in both tables
2. LEFT JOIN - Returns all rows from left table plus matching rows from right table
3. RIGHT JOIN - Returns all rows from right table plus matching rows from left table
4. FULL OUTER JOIN - Returns all rows when there's a match in either table
5. ON - Specifies the join condition between tables

Advanced Operations

1. UNION - Combines results from multiple SELECT statements (removes duplicates)
2. UNION ALL - Combines results from multiple SELECT statements (keeps duplicates)
3. DISTINCT - Removes duplicate rows from the result set
4. CASE WHEN - Creates conditional logic (if-then-else) within SQL queries
5. SUBQUERY (nested SELECT) - Embeds one query inside another for complex filtering or calculations

Data Modification

1. INSERT INTO - Adds new rows to a table
2. UPDATE SET - Modifies existing data in table rows
3. DELETE FROM - Removes rows from a table based on specified conditions
