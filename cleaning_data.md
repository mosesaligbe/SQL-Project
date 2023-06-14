What issues will you address by cleaning the data?

Deleting duplicate data

Removing NULL values

Correcting Logicall Errors

formatting data types




Queries:
Below, provide the SQL queries you used to clean your data.

--removing duplicate data from the all sessions table. 

select  a_n.*

FROM (SELECT a_n.*,

ROW_NUMBER() OVER (partition by fullvisitorid ORDER BY date desc) AS seq
      
FROM analytics a_n
    
) a_n 
   
WHERE seq = 1


-- Correcting logical errors on the Productprice Column in the all_sessions table

ALTER TABLE all_sessions

ALTER COLUMN totaltransactionrevenue TYPE DECIMAl(18,3)

USING totaltransactionrevenue::NUMERIC(18,3);

UPDATE all_sessions

SET totaltransactionrevenue = totaltransactionrevenue / 1000000.0


-- Updating rows in the all_sessions table

UPDATE all_sessions

SET country = NULL

WHERE country = '(not set)'

