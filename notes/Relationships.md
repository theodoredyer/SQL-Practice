## Understanding JOIN
- Most systems automatically generate ID columns that can be used for joining
- Joined query is like a venn diagram where the tables overlap.
- INNER JOIN is what we get when we use the JOIN keyword by itself, contains results where the condition is met in both tables
- LEFT OUTER JOIN = where shared conditions are met + tables in left table without conditions met. 
- FULL OUTER JOIN = completely combining tables. 

## Accessing Related Tables

SELECT l.description AS left, r.description AS right
    FROM left AS l
    LEFT JOIN right AS r ON l.id = r.id
    ;

- Assuming both left and right hold some rows with the same IDs, the result of this JOIN will produce a new table with columns 'left, and right' and their contents for the ID's that match, if we want additionally all of the left content, we use a LEFT JOIN instead, where the condition doesn't match in the right table we'll have NULL fields in the result. 

## Relating Multiple Tables

SELECT c.name AS Cust, c.zip, i.name AS Item, i.description, s.quantity AS Quan, s.price AS Price
  FROM sale AS s
  JOIN item AS i ON s.item_id = i.id
  JOIN customer AS c ON s.customer_id = c.id
  ORDER BY Cust, Item
;

- Where there exist tables customer (which has columns zip, name), item (which has columns name, description), and sale (with column price)
- All of these columns in different tables are linked through their unique IDs which are matched in the JOIN queries.]
- The middle man aka sales table is called the junction table because it links the two customer and item tables. 