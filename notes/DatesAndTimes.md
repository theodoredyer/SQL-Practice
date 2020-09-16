## Dates and Times

- Typically representated in standard SQL format : most sig --> least sig
- YYYY-MM-DD, or HR:MN ( lends well to sorting and searching )
- Stored as UTC (coordinated universal time)

- Doesn't specify types for dates and times, conversion to and from text is minimal
- Every DB system as non standard functinos for handing dates and times.

## Date/Time Functions
- These vary a large amount on each DB system
SELECT DATETIME('now');  = "2019-10-29 21:21:23"
SELECT DATE('now');    = "2019-10-29"
SELECT TIME('now');    = "21:21:25"
SELECT DATETIME('now', '+1 day');    = exactly what you would think
SELECT DATETIME('now', '+3 days');    
SELECT DATETIME('now', '-1 month');    
SELECT DATETIME('now', '+1 year');    
SELECT DATETIME('now', '+3 hours', '+27 minutes', '-1 day', '+3 years');