## Numeric Types
- Data types in one DB are guaranteed to be the same Data types available on another DB system
- How numeric functions work in SQL, probably going to be different in a different system. 
- We have Integer and Real numbers
- INTEGER(precision), DECIMAL(precision, scale), MONEY(precision, scale)
- REAL(precision), FLOAT(precision) these sacrifice accuracy for scale, able to represent VERY large or VERY small
- Precision = number of digits represented, Floats allow large numbers with few significant digits. 


## What Type is that Value?

1 SELECT TYPEOF( 1 + 1 );
2 SELECT TYPEOF( 1 + 1.0 );
3 SELECT TYPEOF('panda');
4 SELECT TYPEOF('panda' + 'koala');

- 1 produces 'integer'
- 2 produces 'real' (integer was converted), result of addition is type real
- 3 produces 'TEXT'
- 4 produces 'integer' (Check the documentation, this doesn't work in SQLite)


## Integer Division

1. SELECT 1 / 2;
2. SELECT 1.0 / 2;
3. SELECT CAST(1 AS REAL) / 2;
4. SELECT 17 / 5;
5. SELECT 17 / 5, 17 % 5;

1. = 0
2. = 0.5
3. = 0.5
4. = 3
5. = 3 and remainder of 2 in a second column


## Rounding Numbers

SELECT 2.55555;     = 2.55555
SELECT ROUND(2.55555);     = 3
SELECT ROUND(2.55555, 3);    = 2.556
SELECT ROUND(2.55555, 0);    = 3

- Supported by all DB systems but syntax may differ