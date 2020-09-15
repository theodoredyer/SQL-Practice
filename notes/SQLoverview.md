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