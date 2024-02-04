# SQL-project1

## EASY LEVEL
## 1-Retrieve all columns for employees with the job title 'Data Analyst'.

select * from employees
where job_title = 'Data Analyst';

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/aad9febb-8923-427f-89a6-e81ae4c143fb)

## 2-List distinct job categories present in the dataset.

select distinct job_category from employees;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/3b75918f-f49f-4bb7-a8f2-8a32a71505f6)

## 3-Find the average salary (in USD) for all job categories.

select job_category, avg(salary_in_usd) from employees
group by job_category;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/14c54b5a-e88b-4ef3-b855-851b9c80162b)

## MODERATE LEVEL
## 1-Identify the top 5 job titles with the highest average salary.

#### select job_title, avg (salary) as avg_sal from employees
#### group by job_title
#### order by avg_sal desc
#### limit 5;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/34a9a845-d968-4c92-9743-b72a9cef9646)

## 2-Calculate the total number of employees for each experience level.

select experience_level, count(*) as total_emp from employees
group by experience_level;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/0e2ab00e-d788-411e-acaf-f8e02712e041)

## 3-Retrieve the job title and salary for employees with a salary greater than $100,000 USD.

select job_title, salary_in_usd from employees
where salary_in_usd > 100000;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/a335429b-0db2-48f8-b842-b5ce97c5d485)

## 4-Determine the average salary for each company size.

select company_size, avg(salary) as avg_sal from employees
group by company_size;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/cfe26eea-5f89-4ca2-b65f-77f0f0673ae9)

## HARD LEVEL
## 1-Find the company location with the highest average salary for Data Scientists.

select company_location, avg(salary) as avg_sal from employees
where job_title = 'Data Scientist'
group by company_location
order by avg_sal desc;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/dcbfd10c-fe4a-4073-bdac-71e3ddb774b8)


## 2-Identify the top 3 job titles with the highest total salary across all companies.

select job_title, sum(salary) as total_sal from employees
group by job_title
order by total_sal desc
limit 3;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/ed310996-1abc-41cb-a37a-8697cd42bfe4)

## 3-Calculate the median salary for each job category.

## 4-Retrieve the job title and salary for employees who work in a remote setting and have an experience level of 'Senior'.

select job_title, salary from employees
where work_setting = 'Remote' AND experience_level = 'Senior';

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/1c2ccb33-0342-4d3b-adb4-6ac8217a8558)

## 5-Find the company size with the highest number of employees.

select company_size, count(*) as total_emp from employees
group by company_size
order by total_emp desc;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/10c30c22-2ce5-4cc6-9336-2312e538b268)

## ADVANCED LEVEL
## 1-Find the job title with the highest salary for employees working in 'Large' companies.

select job_title, max(salary) as high_sal from employees
where company_size = 'L'
group by job_title
order by high_sal desc;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/346a2867-9a5d-45a1-bcbc-c646ff2c4ffc)

## 2-Calculate the salary growth percentage for each job title between the years 2022 and 2023.

select job_title,
((avg(CASE WHEN work_year = 2023 THEN salary END) - avg(CASE WHEN work_year = 2022 THEN salary END))
/
avg(CASE WHEN work_year = 2022 THEN salary END)) 
* 100 AS growth_percent
from employees
where work_year in (2022, 2023)
group by job_title;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/9c2c91fe-03a3-45e6-8eb6-c2a65acd7fea)

## 3-Determine the company location with the highest average salary for employees with an experience level of 'Mid-Level'.

select company_location, avg(salary) as avg_sal from employees
where experience_level = 'Mid-level'
group by company_location
order by avg_sal desc;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/9156a66d-ad6a-4916-977e-ccb796c4e6e1)

## 4-Identify the job title with the highest salary in each job category.

select distinct job_category, job_title, max(salary) from employees
group by job_title, job_category;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/21e825d9-8f90-4ef9-ac64-d35ecd0c1f77)

## 5-Calculate the average salary for employees in each company size, considering only those with an 'Senior' experience level.

select company_size, avg(salary) from employees
where experience_level = 'Senior'
group by company_size;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/d0620650-2b6d-4ebb-8cf1-957ba724d4ed)

## 6-Find the job title with the highest salary increase from the year 2022 to 2024.

select job_title,
(avg(CASE WHEN work_year = 2024 THEN salary END) - avg(CASE WHEN work_year = 2022 THEN salary END)) as increase_sal
from employees
where work_year in (2022, 2024)
group by job_title
order by increase_sal desc;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/34d5f289-31bf-407b-8a81-63af87858c3b)

we are getting NULL values for increase_sal, it could be due to Missing data: the COALESCE function is used to replace potential NULL values with 0.

select job_title,
COALESCE(AVG(CASE WHEN work_year = 2024 THEN salary END), 0) - COALESCE(AVG(CASE WHEN work_year = 2022 THEN salary END), 0) AS increase_sal
from employees
where work_year in (2022, 2024)
group by job_title
order by increase_sal desc;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/cb5c10f5-68c6-492d-a332-d3b6d0520db8)

# SQL Project 2

## Easy Level:
## 1-Retrieve all columns for all rows in the dataset.

select * from aqi;


## 2-Display unique countries present in the dataset.

select distinct country from aqi;


## 3-Count the total number of records in the dataset.

select count(*) as total_records from aqi;


## 4-List all distinct pollutants recorded in the dataset.

select distinct pollutant_id from aqi;


## 5-Retrieve records for a specific city of your choice.

select * from aqi
where city = 'Mumbai';


## Intermediate Level:
## 1-Calculate the average pollutant_avg for each pollutant across all stations.

select distinct pollutant_id, avg(pollutant_avg) as avg_pollutant from aqi
group by pollutant_id;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/e9c1719f-c74e-4a0e-baf9-8cf1fdc2217a)

## 2-Find the station(s) with the highest pollutant_max value and display their details.

select station, max(pollutant_max) as high_pollutant from aqi
group by station;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/fdffc272-38d8-4eff-88cd-7b386c9b9795)

## 3-List the states where the air quality is not recorded (missing entries for pollutant values).

select state from aqi
where pollutant_id is null;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/f7718de6-60c7-43e8-a6e9-7b4d86a2ebb6)

## 4-Retrieve the records where the latitude is greater than a specified value.

select * from aqi
where latitude > 25;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/ade2de7b-21b1-4290-b744-3bfa49632a00)

## 5-Display the city and station with the lowest pollutant_min value.

select city, station, min(pollutant_min) from aqi
group by city, station;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/8d34d2ff-3f67-44ac-946b-7c178d037cd1)

## Advanced Level:
## 1-Identify the country with the highest overall pollutant_avg value.

select country, max(pollutant_avg) from aqi
group by country;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/51101353-4a9c-4e15-b8e5-3cae01bcc982)

## 2-Determine the top 3 cities with the lowest average pollutant_avg values.

select city, min(pollutant_avg) as avg_pollutant from aqi
group by city
order by avg_pollutant
limit 3;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/4cdb5201-6b23-480f-8a3c-55e1244a66de)

## 3-Calculate the percentage change in pollutant_avg from the previous update for a specific station.

## 4-Rank the stations based on their total pollutant_avg values in descending order.

select station, sum(pollutant_avg) as total_avg_pollutant from aqi
group by station
order by total_avg_pollutant desc;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/e48840df-4f4b-4ced-a414-09cbf1123561)

## 5-Find the city where the air quality has shown the most improvement (highest decrease in pollutant_avg).




















