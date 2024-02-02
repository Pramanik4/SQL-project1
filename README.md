# SQL-project1

## EASY LEVEL
## 1-Retrieve all columns for employees with the job title 'Data Analyst'.

#### SELECT * FROM dbo.Employees
#### WHERE job_title = 'Data Analyst';

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/f1afb38b-9786-4c18-984e-d84f1f2e3d1f)

## 2-List distinct job categories present in the dataset.

#### SELECT DISTINCT job_title FROM dbo.Employees;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/fcd00442-d755-435d-afed-a6cc3a361468)

## 3-Find the average salary (in USD) for all job categories.

#### SELECT job_category, AVG(salary_in_usd) FROM dbo.Employees
#### GROUP BY job_category;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/39cc49f2-ab67-4520-98c8-a9a0a507273c)

## MODERATE LEVEL
## 1-Identify the top 5 job titles with the highest average salary.

#### SELECT TOP 5 job_title, AVG(salary) AS avg_salary FROM dbo.Employees
#### GROUP BY job_title
#### ORDER BY avg_salary DESC;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/bc3ce210-9489-4dab-925e-240d1b890ee6)

## 2-Calculate the total number of employees for each experience level.

#### select experience_level, count(experience_level) from dbo.Employees
#### group by experience_level;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/5fdb02dd-ecfe-4cef-bd47-9e0c76f13e03)

## 3-Retrieve the job title and salary for employees with a salary greater than $100,000 USD.

#### select job_title, salary_in_usd from dbo.Employees
#### where salary_in_usd > 100000;

![image](https://github.com/Pramanik4/SQL-project1/assets/75212387/8c401522-224a-47a2-953f-e12b8e2fb2ea)

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


















