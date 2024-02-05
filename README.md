1. List out the total number of daily confirmed cases of all countries and territories in descending order.
```SQL
SELECT	
sum(daily_confirmed_cases) as `daily_confirmed_cases`, countries_and_territories 
FROM `bigquery-public-data.covid19_ecdc_eu.covid_19_geographic_distribution_worldwide` 
Group by 2
Order by 1 DESC
```
![Screenshot 2024-02-05 181943](https://github.com/Archana1819/Archana1819/assets/159028840/cb462bdd-c7f9-4496-b364-445508f60dfa)

2. Find out the total deaths in India
```SQL
SELECT	
sum(deaths) as `Total deaths`,
FROM `bigquery-public-data.covid19_ecdc_eu.covid_19_geographic_distribution_worldwide` 
where countries_and_territories = "India" 
```
![Screenshot 2024-02-05 182437](https://github.com/Archana1819/Archana1819/assets/159028840/73241ad6-99b9-465c-8465-ab094173a203)

