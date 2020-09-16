## What are Transactions? 
- Transaction = group of operations that are handles as one unit of work
- Many operations, if any of them fails the entire group fails and the DB restores to pre-operation state

BEGIN TRANSACTION
    INSERT INTO tab1
    INSERT INTO tab2
    etc
    ...
END TRANSACTION

- Concurrent operations result in a state as if they wre handles sequentially and separately. 
- Can sometimes radically improve performance, individual writes are much slower than groups of inserts as transactions
- DB system can perform many operations together
- Improve reliability and performance. 


## Data Integrity - Transaction Example

- Set up tables
- Insert values into inventory
- Make a transaction for producing a sale that also modifies the inventory

CREATE TABLE widgetInventory (
  id INTEGER PRIMARY KEY,
  description TEXT,
  onhand INTEGER NOT NULL
);

CREATE TABLE widgetSales (
  id INTEGER PRIMARY KEY,
  inv_id INTEGER,
  quan INTEGER,
  price INTEGER
);

INSERT INTO widgetInventory ( description, onhand ) VALUES ( 'rock', 25 );
INSERT INTO widgetInventory ( description, onhand ) VALUES ( 'paper', 25 );
INSERT INTO widgetInventory ( description, onhand ) VALUES ( 'scissors', 25 );

SELECT * FROM widgetInventory;
SELECT * FROM widgetSales;

BEGIN TRANSACTION;
INSERT INTO widgetSales ( inv_id, quan, price ) VALUES ( 1, 5, 500 );
UPDATE widgetInventory SET onhand = ( onhand - 5 ) WHERE id = 1;
END TRANSACTION;
- Sell 5 rocks and update inventory and sales in the same step. 

BEGIN TRANSACTION;
INSERT INTO widgetInventory ( description, onhand ) VALUES ( 'toy', 25 );
ROLLBACK;
SELECT * FROM widgetInventory;


- Many different SQL versions have different syntax for transactions, often times they will accept multiple forms of syntax
- If we need to rollback a transaction do the above ^



## Performance
- Transactions commonly used to increase performance, they make things much faster
- Up to 20x or more