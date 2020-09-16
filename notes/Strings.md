## About SQL Strings

- Literal strings expressed by a series of characters within single quotes, MySQL uses double quotes. 
- To put a single quote in your string, use two single quotes '' produces one 
- String concatenation works differently in most versions of SQL.

## Finding Length
SELECT LENGTH('string');
- This produces 6

SELECT Name, LENGTH(Name) AS Len FROM City ORDER BY Len DESC, Name;
- This produces a list of city names as one column, length as another column, and sorts by the length of the city names. 

## Selecting Part of a String
- SQL Standard doesn't have a substring method, but most DB systems have one
SELECT SUBSTR('this string', 6, 3);
- produces 'string' aka everything from the 6th position till the end, second arg is the number of characters to return.

SELECT released FROM album ORDER BY released;
- Produces YYYY-MM-DD
SELECT released
    SUBSTR(released, 1, 4) AS Year,
    SUBSTR(released, 6, 2) AS Month,
    SUBSTR(released, 9, 2) AS Day
    FROM album ORDER BY released
    ;

- This splits up the string into 
- Year (YYYY), Month (MM), Day (DD)
- All major DB engines have something like this. 


## Removing Spaces
SELECT TRIM('    string   ');
SELECT LTRIM('    string    ');
SELECT RTRIM('   string   ');
SELECT TRIM('...string...', '.'); (this removes all of the second specified characters from the input string)
- Useful for processing user input where users don't recognize spaces are significant


## Folding Case
- SELECT 'StRiNg' = 'string';   ( Produces a 0 because these two are not equivalent)
- SELECT LOWER('StRiNg') = LOWER('string');     (Produces a 1 because the lower case of these two strings are equal)
- SELECT UPPER('StRiNg') = UPPER('string');   ( ^^ )
- SELECT UPPER(Name) FROM City ORDER BY Name;
- SELECT LOWER(Name) FROM City ORDER BY Name;