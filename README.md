# Day 1 - 04 Feb 2025

1) Installation of sqlite studios from the official [site](https://sqlitestudio.pl/)
2) Downloading dump database from the [link](https://github.com/davidjamesknight/SQLite_databases_for_learning_data_science/blob/main/tips.db)
3) Load rge the dump database to sqlite studio
    - Step 1: click on add database
    - step 2: select create new database then
    - Step 3: select the downloaded database and click ok
    - step 4: dataset will be add 
4) Querying the loaded data
5) Generated sample questions using chatgpt
    - login to [ChatGPT](https://openai.com/index/chatgpt/)
    - Upload the database dump to chatgpt to analyze
    - Written the prompt to generate sample questions
        ```
        Generate few sqlite quest on the given database 
        ```
6) Used chatgpt to understand few unknown topic in sql
     - Upload the question you have doughts in
    ```
        Explain the above question in detail
    ```


## Exercise

***Fetch all the data from table: Day***

```sql
select * from Day;
```
***Fetch all the data from table: Smoker***
```sql
SELECT * FROM Smoker;
```
***Fetch all the data from table: Time***
```sql
select * from Time;
```
***Fetch all the data from table: Gender***
```sql
select * from sex;
```
***Fetch all the data from table***
```sql
select * from observation;
```
***The average tip given by customer***
```sql
SELECT AVG(tip) from Observation;
```
***The tip amount based on the day of the week***
```sql
SELECT Day.day , AVG(Observation.tip) AS avg_tip
FROM Observation
JOIN DAY ON Observation.day_id= Day.day_id
GROUP BY Day.day
ORDER BY avg_tip DESC;
```
***The Smoker tips are more or non smokers***
```sql
SELECT Smoker.smoker, AVG(Observation.tip) AS avg_tip
from observation
JOIN Smoker ON Observation.smoker_id= Smoker.smoker_id
GROUP BY Smoker.smoker
ORDER BY avg_tip DESC;
```
***Diff in tips b/w male and female***
```sql
SELECT Sex.sex, AVG(Observation.tip) AS avg_tip
from observation
JOIN Sex ON Observation.sex_id=Sex.sex_id
GROUP BY Sex.sex;
```
***The more tipps in lunch or dinner***
```sql
SELECT Time.time , AVG(Observation.tip) AS avg_tip
from observation
join Time on observation.time_id=Time.time_id
group by Time.time;
```
***The day of the week with highest tip***
```sql
SELECT Day.day ,AVG(Observation.tip) as avg_tip
from observation
join Day on observation.day_id= Day.day_id
group by Day.day
order by avg_tip DESC;
```
***The highest bill***
```sql
select total_bill, AVG(tip) as avg_tip
from observation
group by total_bill
order by total_bill desc
limit 5;
```
***The lowest bill***
```sql
select total_bill, AVG(tip) as avg_tip
from observation
group by total_bill
order by total_bill asc
limit 5;
```
***detemine 10 smokers***
```sql
SELECT * FROM Observation 
WHERE smoker_id = 1 
limit 10;
```
***where total more than 20 and tip is more than 5 both***
```sql
SELECT * FROM Observation 
WHERE total_bill > 20 AND tip > 5;
```
***Finding the max values***
```sql
select max(tip) as highest_tip from observation;
```
***Finding the min value***
```sql
select min(total_bill) as lowest_total from observation;
```
***Converting into lowers***
```sql
select lower(smoker) from smoker;
```
***replace letters***
/*replace*/
```sql
select replace(sex,'al','abc') from sex;
```
***generating random number***
```sql
select random() as random_no;
```
***write a query to categorize cutomers based on the tip amount***
```sql
select tip,
case
when tip>5 then 'high tip'
when tip between 3 and 5 then 'medium tip'
else 'low tip'
end as tip_category
from Observation
order by tip desc;
```
***write a query to display weekend for saturday and sunday and weekday for rest***
```sql
select day,
case
when day in ('saturday','sunday')then 'weekend'
else 'weekday'
end as day_type 
from day;
```
***Round the average tip amount to 2 decimal places***
```sql
select round(avg(tip),2) as avg_tip_rounded from observation;
```
***Replace the word "Yes" with "Smoker" and "No" with "Non-Smoker" in the Smoker table.***
```sql
update smoker
set smoker = case
when smoker='yes' then 'smoker'
when smoker='no' then'non-smoker'
else smoker
end;
```
***Retrieve the first 3 characters of each day's name from the Day table***
```sql
select substr(day,1,3) as short_day from day;
```
***Retrieve the first 3 characters of each day's name from the Day table.***
```sql
select upper(sex) from sex;
```
***Find the total revenue (sum of total_bill) generated per day***
```sql
select sum(total_bill) as total_revenue from observation;
```
***Write a query to find the total number of records in the Observation table***
```sql
select count(*) as total_observations from observation;
```
