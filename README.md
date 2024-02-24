
## Table of Contents

1. [SQL Project 1](#sql-project1)
2. [SQL Project 2](#sql-project2)


# SQL-project 1

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

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/92bdee65-68cf-43fe-8c6b-985f13ccf798)

## 2-Display unique countries present in the dataset.

select distinct country from aqi;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/c86babca-41ea-4a77-8caa-df5e5e3b03ca)

## 3-Count the total number of records in the dataset.

select count(*) as total_records from aqi;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/aaaa0e93-7e9e-49c7-8aee-a1e7643f58d6)

## 4-List all distinct pollutants recorded in the dataset.

select distinct pollutant_id from aqi;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/7e873034-aa6d-4984-ab61-1174ec1dd6b3)

## 5-Retrieve records for a specific city of your choice.

select * from aqi
where city = 'Mumbai';

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/a47f802c-281c-497d-9c90-787a741fcb82)

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

#### EXTRA
## Count the total number of columns in the dataset.

SELECT COUNT(*) AS total_columns
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_NAME = 'aqi';

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/b9e0bbdf-305a-4801-a410-304f29d9518b)

# SQL Project3

## Easy:
## 1-Retrieve the names of all tracks released in the year 2021.

select track_name, released_year from music
where released_year = 2021;

![image](https://github.com/Pramanik4/SQL-projects/assets/75212387/c47373a4-dfb5-41c6-a680-ae5f8d56d87d)

## 2-Find the total number of streams for all tracks in the dataset.

select track_name, sum(streams) from music
group by track_name;

![image](https://github.com/Pramanik4/SQL-projects/assets/75212387/2870f5c4-e5db-4f19-a062-e11ca516f7b4)

## 3-List the distinct musical keys present in the dataset.



## 4-Count the number of tracks that are present in Spotify playlists.

select count(track_name) as No_tracks from music;

![image](https://github.com/Pramanik4/SQL-projects/assets/75212387/02c3ffca-abe6-4c8a-9624-8ebbb5b75795)

## 5-Find the tracks with the highest danceability percentage.



## Intermediate:
## 1-Calculate the average energy percentage for tracks released in 2020.
## 2-Identify the top 5 artists with the most tracks in Spotify charts.
## 3-List the tracks with the highest instrumentalness percentage.
## 4-Find the total number of streams for tracks in both Spotify and Apple Music playlists.
## 5-Retrieve the tracks released in the month of May.

## Advanced:
## 1-Identify the artist(s) with the highest average valence percentage.
## 2-List the top 10 tracks with the most streams in Spotify charts.
## 3-Find the tracks with danceability percentage above 80% and energy percentage below 60%.
## 4-Calculate the average acousticness percentage for tracks in Deezer charts.
## 5-Retrieve the tracks released on a weekend (Saturday or Sunday).

## Expert:
## 1-Identify the artist(s) with the highest total streams across all their tracks.
## 2-Find the tracks that are present in both Apple Music and Deezer charts.
## 3-Calculate the median danceability percentage for all tracks.
## 4-Identify the tracks with the highest liveness percntage in Spotify playlists.
## 5-Find the tracks with the highest speechiness percentage in Shazam charts.


# SQL Project 4

![image](https://github.com/Pramanik4/SQL-projects/assets/75212387/fd188dba-cec8-4b8a-a899-af4944ba3203)

## 1. Retrieve all employees' information.

![image](https://github.com/Pramanik4/SQL-projects/assets/75212387/6c00238d-1579-48b7-9d6d-24a5acd93ed7)

## 2. Retrieve the names of all employees in the Sales department.

![image](https://github.com/Pramanik4/SQL-projects/assets/75212387/149b922d-9f9c-44a3-b5b8-54802f7bec4f)

## 3. Retrieve the total number of employees in each department.

![image](https://github.com/Pramanik4/SQL-projects/assets/75212387/58f875b8-561a-4e4c-8779-d8b0f4757fe4)

SELECT MAX(emp_salary) AS highest_salary FROM employees;

![image](https://github.com/Pramanik4/SQL-projects/assets/75212387/5f56d66b-8adb-4bb6-add4-f72ffcd3efff)

Retrieve the average salary of all employees.

![image](https://github.com/Pramanik4/SQL-projects/assets/75212387/9bd5aa99-d1f1-4f2f-8bcf-2f056727aeac)

Retrieve the employee with the highest salary.

![image](https://github.com/Pramanik4/SQL-projects/assets/75212387/9adcdc0e-9b00-4a3b-a9e5-941eae08ced7)

Retrieve the names of employees whose salaries are above 55000.

![image](https://github.com/Pramanik4/SQL-projects/assets/75212387/faac9a6f-25ea-424f-b740-a9638cad9162)

Combined two tables and give it a name

![image](https://github.com/Pramanik4/SQL-projects/assets/75212387/189aaee7-f769-4ec6-b085-77551474c90c)

Retrieve the total salary expense for the Sales department.

![image](https://github.com/Pramanik4/SQL-projects/assets/75212387/6f35aaf9-2385-4354-b913-046a33df3e1d)

Retrieve the employee(s) with the lowest salary.

![image](https://github.com/Pramanik4/SQL-projects/assets/75212387/f0f2ac6d-6c5e-4330-89cc-c28c3057ed0c)

Retrieve the department(s) with more than 2 employees.

![image](https://github.com/Pramanik4/SQL-projects/assets/75212387/ce7dcd9f-d4f7-469e-9995-89cd911d6f50)

Retrieve the department(s) where no employee earns more than 60000.

![image](https://github.com/Pramanik4/SQL-projects/assets/75212387/534f39df-0ec2-4390-8baa-a5cb99d9fb20)


































