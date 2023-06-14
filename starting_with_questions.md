Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:
SELECT SUM(totaltransactionrevenue) AS highest_level_of_transaction, currencycode, country, city, timeonsite
FROM all_sessions
WHERE totaltransactionrevenue IS NOT NULL AND city != 'not available in demo dataset'
GROUP BY totaltransactionrevenue, currencycode,city, country, timeonsite
ORDER BY totaltransactionrevenue DESC


Answer:
<img width="778" alt="image" src="https://github.com/mosesaligbe/SQL-Project/assets/30363635/d6866e97-d17c-46ca-9582-fe45394f6199">






**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:



Answer:





**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:



Answer:





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:



Answer:





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:



Answer:







