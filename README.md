# SQL-project1

## EASY LEVEL
## 1-Retrieve all columns for employees with the job title 'Data Analyst'.

select * from employees
where job_title = 'Data Analyst';

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/aad9febb-8923-427f-89a6-e81ae4c143fb)


## 2-List distinct job categories present in the dataset.

#### SELECT DISTINCT job_title FROM dbo.Employees;

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

#### select experience_level, count(experience_level) from dbo.Employees
#### group by experience_level;

select experience_level, count(*) as total_emp from employees
group by experience_level;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/0e2ab00e-d788-411e-acaf-f8e02712e041)

## 3-Retrieve the job title and salary for employees with a salary greater than $100,000 USD.

select job_title, salary_in_usd from employees
where salary_in_usd > 100000;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/a335429b-0db2-48f8-b842-b5ce97c5d485)

# START

## 4-Determine the average salary for each company size.

#### select company_size, avg(salary) from dbo.Employees
#### group by company_size;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/44114c59-203d-4013-a029-0c7f56fa0f14)

## HARD LEVEL
## 1-Find the company location with the highest average salary for Data Scientists.

#### select company_location, avg(salary) as avg_sal from dbo.Employees
#### where job_title = 'Data Scientist'
#### group by company_location
#### order by avg_sal desc;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/ea72f08a-bee2-4b54-91b3-d7f7c53bd100)

## 2-Identify the top 3 job titles with the highest total salary across all companies.

#### sselect top 3 job_title, sum(salary) as total_sal from dbo.Employees
#### group by job_title
#### order by total_sal desc;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/3e622b15-195e-4da4-b1e6-eb53c5a6a5f1)

## 3-Calculate the median salary for each job category.

## 4-Retrieve the job title and salary for employees who work in a remote setting and have an experience level of 'Senior'.

#### select job_title, salary from dbo.Employees
#### where work_setting = 'Remote' and experience_level = 'Senior';

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/7a38b18f-e3ef-432d-8c39-20015ed94461)

## 5-Find the company size with the highest number of employees.

#### select company_size, count(*) as emp_count from dbo.Employees
#### group by company_size
#### order by emp_count desc;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/2f1318fc-8f97-437b-9fe4-4be6ef71cf4d)

## ADVANCED LEVEL
## 1-Find the job title with the highest salary for employees working in 'Large' companies.

#### select job_title, max(salary) as high_sal from dbo.Employees
#### where company_size = 'L'
#### group by job_title
#### order by high_sal desc;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/ef0d23a7-78b4-43f1-95a6-f399cdf46f47)

## 2-Calculate the salary growth percentage for each job title between the years 2022 and 2023.

## 3-Determine the company location with the highest average salary for employees with an experience level of 'Mid-Level'.

#### select company_location, avg(salary) as avg_sal from dbo.Employees
#### where experience_level = 'Mid-level'
#### group by company_location
#### order by avg_sal desc

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/5da1b05d-ea94-4b4d-81cd-28f7596180a5)

## 4-Identify the job title with the highest salary in each job category.

#### select distinct job_category,job_title, max(salary) from dbo.Employees
#### group by job_category,job_title

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/71a0ddd0-dbf4-435c-8790-015b9afd6beb)

## 5-Calculate the average salary for employees in each company size, considering only those with an 'Senior' experience level.

#### select company_size, avg(salary) as avg_sal from dbo.Employees
#### where experience_level = 'Senior'
#### group by company_size;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/1d1e98a8-9fe9-4a16-b6aa-e0c48bed83bb)

## 6-Find the job title with the highest salary increase from the year 2022 to 2024.


















