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

3. What is the minimum and maximum confirmed cases?
```SQL
SELECT min(confirmed_cases) as`Minimum confirmed cases`, max(confirmed_cases)as `Maximum confirmed cases` FROM `bigquery-public-data.covid19_ecdc_eu.covid_19_geographic_distribution_worldwide` 
```
![Screenshot 2024-02-05 183017](https://github.com/Archana1819/Archana1819/assets/159028840/4987e7d9-b974-49b6-8d7d-406f91be3471)

4. Find out the total deaths and confirmed cases where date is 31/10/2020
```SQL
SELECT SUM(confirmed_cases) AS `total_confirmed_cases`, SUM(deaths) AS `total_deaths`,
FROM `bigquery-public-data.covid19_ecdc_eu.covid_19_geographic_distribution_worldwide` 
where date = "2020-10-31" 
```
![Screenshot 2024-02-05 183724](https://github.com/Archana1819/Archana1819/assets/159028840/3a11dfcb-b8d9-4070-aab9-878bb6b7110a)

5. Number of countries with confirmed cases is null for the entire pandemic.
```SQL
SELECT count(countries_and_territories)as `number of countries`
  FROM `bigquery-public-data.covid19_ecdc_eu.covid_19_geographic_distribution_worldwide` 
where confirmed_cases is null
```
![Screenshot 2024-02-05 184509](https://github.com/Archana1819/Archana1819/assets/159028840/51875471-238f-4e00-9724-0165096a9691)

6. Average confirmed cases for each month in 2020
```SQL
SELECT month, AVG(confirmed_cases) AS `avg_confirmed_cases`
FROM `bigquery-public-data.covid19_ecdc_eu.covid_19_geographic_distribution_worldwide` 
WHERE year = 2020
GROUP BY month
```
![Screenshot 2024-02-05 184822](https://github.com/Archana1819/Archana1819/assets/159028840/e57d91ac-ac36-493e-b1d5-65135e66d9ea)

7. Find the top 5 countries which have highest number of confirmed cases on 19 July 2020.
```SQL
SELECT countries_and_territories, SUM(confirmed_cases) as ` Total confirmed cases`
FROM `bigquery-public-data.covid19_ecdc_eu.covid_19_geographic_distribution_worldwide` 
WHERE date= "2020-07-19"
GROUP BY countries_and_territories
Order by SUM(confirmed_cases) DESC
LIMIT 5
```
![Screenshot 2024-02-05 185637](https://github.com/Archana1819/Archana1819/assets/159028840/3de56ca7-43b6-44e1-a739-c94ce1336001)

8. Find the date with the highest number of confirmed cases
```SQL
SELECT date, confirmed_cases
FROM `bigquery-public-data.covid19_ecdc_eu.covid_19_geographic_distribution_worldwide` 
ORDER BY confirmed_cases DESC
LIMIT 1
```
![Screenshot 2024-02-05 190001](https://github.com/Archana1819/Archana1819/assets/159028840/5f309f97-5953-428e-ad56-1086905397ff)
  
9. Find out percent_of_baseline on 16 April 2020. 
```SQL
SELECT a.date, a.percent_of_baseline
FROM `bigquery-public-data.covid19_ecdc_eu.covid_19_geographic_distribution_worldwide` c
Left join `bigquery-public-data.covid19_geotab_mobility_impact_eu.airport_traffic` a
on c.date=a.date
where c.date = "2020-04-16"
```
![Screenshot 2024-02-05 191933](https://github.com/Archana1819/Archana1819/assets/159028840/875df050-9574-4097-a9cd-e5922feb9318)

10. Find out the percent of baseline of Australia on 20 March 2020. 
```SQL
SELECT a.country_name, a.percent_of_baseline,a.date
FROM `bigquery-public-data.covid19_ecdc_eu.covid_19_geographic_distribution_worldwide` c
Left join `bigquery-public-data.covid19_geotab_mobility_impact_eu.airport_traffic` a
on c.countries_and_territories =a.country_name
where c.countries_and_territories = "Australia" and a.date = "2020-03-20"
```
![Screenshot 2024-02-05 192535](https://github.com/Archana1819/Archana1819/assets/159028840/6536dc88-63a8-424a-a458-cf9e529aded6)
