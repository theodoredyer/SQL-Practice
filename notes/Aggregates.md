## What are Aggregates?

- SQL has powerful features for handling aggregate data.

SELECT COUNT(*) FROM Country; - this is an aggregate function

SELECT Region, COUNT(*) AS Count
    FROM Country
    GROUP BY Region
    ORDER BY Count DESC, Region
;

Antarctica   5
 Australia    5
 British Islands    2 
 etc

- The groupby allows us to apply the aggregate COUNT to specific groups rather than the whole

- Works for JOIN queries aswell.

SELECT a.title AS Album, COUNT(t.track_number) as Tracks
  FROM track AS t
  JOIN album AS a
    ON a.id = t.album_id
  GROUP BY a.id
  HAVING Tracks >= 10
  ORDER BY Tracks DESC, Album
;

- WHERE clauses should be before your GROUP BY clauses because they occur before the aggregation
- HAVING occurs on the aggregated data, so it should take place AFTER
- HAVING is for aggregate data, WHERE is for non aggregated. 
- Aggregate fucntions operate on multiple rows rather than multiple. 

## Using aggregate functions

SELECT COUNT(*) FROM Country;      = Count of all rows in the table
SELECT COUNT(Population) FROM Country;   = Counts the non null values within that column
SELECT AVG(Population) FROM Country;    = Average value for a column with numerical values
SELECT Region, AVG(Population) FROM Country GROUP BY Region;     = 
SELECT Region, MIN(Population), MAX(Population) FROM Country GROUP BY Region;
SELECT Region, SUM(Population) FROM Country GROUP BY Region;



## Aggregating DISTINCT values

SELECT COUNT(HeadOfState) FROM Country;    = Count of rows in the db that have a value for HeadOfState
SELECT HeadOfState FROM Country ORDER BY HeadOfState;
SELECT COUNT(DISTINCT HeadOfState) FROM Country;

- Distinct used to fold duplicates before the aggregate is called. 
- Sometimes distinct is replaced by UNIQUE