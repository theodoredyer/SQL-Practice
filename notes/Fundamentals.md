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
