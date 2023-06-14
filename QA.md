What are your risk areas? Identify and describe them.

Blank or Null values

Duplicate Values

Inconsistent data types


QA Process:
Describe your QA process and include the SQL queries used to execute it.

I replaced empty rows with NULL values. For example in the city column under the all_session table using the query below:

UPDATE all_sessions 

SET city = NULL

WHERE city = '(not set)';

I eliminated duplicate data using the query below:

select  a_n.*

FROM (SELECT a_n.*,

ROW_NUMBER() OVER (partition by fullvisitorid ORDER BY date desc) AS seq
      
FROM analytics a_n
    
) a_n 
   
WHERE seq = 1;


I converted columns to reasonable data types. For example the timeonsite column, I convert it from Varchar to time using the query below:

ALTER TABLE all_sessions

ALTER COLUMN timeonsite

TYPE VARCHAR

USING LPAD(timeonsite::VARCHAR, 6, '0');

UPDATE all_sessions

SET timeonsite = CONCAT(
    SUBSTRING(timeonsite, 1, 2),
    ':',
    SUBSTRING(timeonsite, 3, 2),
    ':',
    SUBSTRING(timeonsite, 5, 2)
);

update all_sessions

set timeonsite = NULL

where timeonsite = '::';

UPDATE all_sessions

SET timeonsite = TIME '00:00:00' + 
           INTERVAL '1 hour' * CAST(SUBSTR(timeonsite, 1, 2) AS INTEGER) +
           INTERVAL '1 minute' * CAST(SUBSTR(timeonsite, 4, 2) AS INTEGER) +
           INTERVAL '1 second' * CAST(SUBSTR(timeonsite, 7, 2) AS INTEGER);

