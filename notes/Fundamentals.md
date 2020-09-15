## Creating a Table

CREATE TABLE test (
    a INTEGER,
    b TEXT
);

INSERT INTO test VALUES (1, 'a' );
INSERT INTO test VALUES (2, 'b' );
INSERT INTO test VALUES (3, 'c' );

SELECT * FROM test;

- The column definitions within the CREATE TABLE are the schema
- Columns are named a and b with their types.

## Deleting a table
DROP TABLE test;
DROP TABLE IF EXISTS test;

## Inserting Rows
CREATE TABLE test1 (a INTEGER, b TEXT, c TEXT );

INSERT INTO test VALUES(1, 'This', 'Here');
or
INSERT INTO test (b, c) VALUES ('text', 'text2');
or
INSERT INTO test DEFAULT VALUES;
or
Use the results from a select statement to add rows
INSERT INTO test (a, b, c) SELECT id, name, description from item; ( adds all rows from item)

## Deleting Rows
DELETE FROM test WHERE a = 3;
(deletes all rows that have 'a' value of three)

## The NULL Value
- Not a value, it is the lack of a value. 
- If you try to "WHERE a = NULL" it won't work because its not a value
- to test for null, use IS NULL
SELECT * FROM test WHERE a IS NULL;
SELECT * FROM test WHERE a IS NOT NULL;

- Empty string & 0 are different from NULL

CREATE TABLE test (
    a INTEGER NOT NULL,
    b TEXT NOT NULL,
    c TEXT NOT NULL
);

^ this enforces that the values in your table cannot be null, creation of rows not including values in each column will produce an error.

## Constraining Columns

DROP TABLE IF EXISTS test;

CREATE TABLE test (a TEXT, b TEXT, c TEXT NOT NULL);
INSERT INTO test (a, b) VALUES ('one', 'two');
SELECT * FROM test;

CREATE TABLE test (a TEXT UNIQUE, b TEXT, c TEXT DEFAULT 'panda');

- Constraints create rules for the values that can be held in a table

## Changing a Schema

ALTER TABLE test ADD d TEXT;
- This adds a column to an existing table with NULL values in all fields of the previous table
- Alternatively can add constraints just as in a regular defintion for default values.


## ID Columns
- A column that holds a unique value for each row in a table
- Method for creating one is not standardized

DROP TABLE IF EXISTS test;

CREATE TABLE test (
    id INTEGER PRIMARY KEY,
    a INTEGER,
    b TEXT
)

INSERT INTO test (a, b) VALUES (10, 'a');
SELEXT * FROM test;

- ID values are automatically generated.
- Most versions of SQL have different ways of doing this

## Filtering Data
- WHERE clause allows us to filter

Select Name, Continent, Population FROM Country WHERE Population < 100000 OR Population IS NULL ORDER BY Population DESC;

- Can use AND and OR clauses to add multiple conditions into a WHERE clause

SELECT Name, Continent, Population FROM Country WHERE Name LIKE '%island%';
- ^ Selects all rows whose names contain 'island'
SELECT Name, Continent, Population FROM Country WHERE Name LIKE '_a%';
- ^ Selects all rows whose names contain words where a is the second letter

SELECT Name, Continent, Population FROM Country WHERE Continent IN ('Europe', 'Asia');
- IN specifies a range as opposed to the = in a regular WHERE

## Removing Duplicates
SELECT DISTINCT Continent FROM Country; 
- Only produces one entity of each result, UNIQUE results. 

## Ordering Output
SELECT Name FROM Country;
ORDER BY Name (ASC, DESC)
ORDER BY Continent, Name;
- Sorts the results of queries. 

## Conditional Expressions
CREATE TABLE booltest (a INTEGER, b INTEGER);
INSERT INTO booltest VALUES (1,0);
SELECT * FROM booltest;

SELECT 
    CASE WHEN a THEN 'true' ELSE 'false' END as boolA,
    CASE WHEN b THEN 'true' ELSE 'false' END as boolB
    FROM booltest
;

SELECT 
    CASE a WHEN 1 THEN 'true' ELSE 'false' END AS boolA,
    CASE b WHEN 1 THEN 'true' ELSE 'false' END AS boolB
    FROM booltest
;


