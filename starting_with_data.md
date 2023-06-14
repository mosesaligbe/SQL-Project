Question 1: 

find the total number of unique visitors 

SQL Queries:

SELECT DISTINCT(COUNT(fullvisitorid)) AS total_unique_visitors

FROM all_sessions;

Answer: 


<img width="320" alt="image" src="https://github.com/mosesaligbe/SQL-Project/assets/30363635/4a60fa3e-c788-41ea-aad6-73828ff1e3a9">





Question 2: 

what date was the highest totaltransactionrevenue recorded ?


SQL Queries:

SELECT date, totaltransactionrevenue

FROM all_sessions

WHERE totaltransactionrevenue IS NOT NULL

ORDER BY totaltransactionrevenue DESC

Answer:

<img width="320" alt="image" src="https://github.com/mosesaligbe/SQL-Project/assets/30363635/79b4ee3d-c7e3-47d7-bf12-d6140a172458">



Question 3: 

SQL Queries:

Answer:



Question 4: 

SQL Queries:

Answer:



Question 5: 

SQL Queries:

Answer:
