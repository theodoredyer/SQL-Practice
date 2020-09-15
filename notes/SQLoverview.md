## About SQL

SQL is designed for the opertions and management of relational databases. Simple language with simple syntax.

SELECT * FROM Countries WHERE Continent = 'Europe';

WHERE clause requires an expression that evaluates to a value. 


### Fundamental Operations

- Create
- Read
- Update
- Delete

SELECT used for all queries that return values. How we get data from the database, the 'R' in CRUD

INSERT used to add a row to a table

UPDATE used to change data

DELETE used to remove rows from a table, where clause used to select which to delete. 


## Database Organization

- Databases have TABLES
- Tables have ROWS and COLUMNS

ROW is like an individual record, each row has a unique key (ID)
COLUMN is like a field.
PRIMARY KEY = column used as the unique key for each row

KEYS create relationships between tables. Sale table might have item_id column to refer to the ID of an item table. 


## The SELECT statement
SELECT 'Hello, World';

- Literal strings are distinguished by single quotes
- Semicolon is required in standard SQL but not always in practice. 
- Used to return the results of a query

SELECT Name, LifeExpectancy AS "Life Expectancy" FROM Country ORDER BY Name;


## Selecting Rows

SELECT Name, Continent, Region FROM Country WHERE Continent = 'Europe' ORDER BY Name LIMIT 5 OFFSET 5;

- This will produce these three columns for every single row in the Country table. 
- Use the WHERE clause to get specific rows
- LIMIT and OFFSET used to select portions of the results
- Order must follow FROM -> WHERE -> ORDER BY -> LIMIT/OFFSET

## Selecting Columns

SELECT * FROM Country; 

- Gives all rows and columns

SELECT Name AS Country, Continent, Region FROM Country;

- Gives just those three columns
- AS used to create an alias
- Order of selection doesn't matter

## Counting Rows

SELECT COUNT(*) FROM Country WHERE Population > 1000000 AND Continent = 'Europe';

- Produces the count of the number of rows in the country table.
- Putting a column name inside COUNT() gives the count of rows for which that field has data


## Inserting Data
SELECT * FROM customer;

INSERT INTO customer (name, address, city, state, zip)
    VALUES ('Theodore Dyer', '123 address st', 'santa clara', 'CA', '12345');

- INSERT INTO does exactly what you would think, where the first parentheses define the columns of data, and the values are the specific values I'm inserting.
- If certain columns are omitted, the resulting entry will have NULL values in the table

## Updating Data
SELECT * FROM customer;

UPDATE customer SET address = '123 Music Ave', zip = '91254' WHERE id = 5;
UPDATE customer SET address = NULL, zip = NULL WHERE id = 5;

- Edits the fields for address and zip for the entry where id = 5

## Deleting Data

SELECT * FROM customer WHERE id = 4;

DELETE FROM customer WHERE id = 4;
SELECT * FROM customer;
