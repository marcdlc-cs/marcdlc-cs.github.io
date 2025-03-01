---
title: Investigating Logins With SQL
permalink: /sql
parent: 🚨 Incident Response
has_toc: false
---
# Investigating Logins With SQL
{: .no_toc }

{: .note }
Incident Investigation, Data Analysis, Security Event Monitoring, Basic SQL Proficiency
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
I work as a security professional at a large organization where I investigate security concerns to ensure system safety. Lately, I've come across potential security problems related to login attempts and employee devices. My task involves analyzing data within the employees and log_in_attempts tables. To do this, I'll utilize SQL filters to extract information from various datasets, enabling me to delve into the possible security threats.

## Objectives
Use SQL filters to retrieve records from different datasets and investigate the potential security issues

## Results
### 📄 Task 1: Retrieve after hours failed login attempts

I need to investigate a potential security incident that occured after business hours. To query the relevant data, I used the following commands:
```sql
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00' AND success = 0
ORDER BY login_time;
```

{: .note2 }
> SELECT with an asterisk returns all columns in the table. FROM specifies which table is being queried. WHERE, along with the proper comparison (>) and logical (AND) operators, filters the displayed results by limiting them to failed login times after 6PM. 
>
> "login_time > 18:00" limits the data to only login times greater than 18:00 (6PM).
>
> In the "success" column of the table, a failed login attempt has a value of 0, and so "success = 0" limits data to only failed login attempts.
>
> ORDER BY organizes the results by login time in descending order.


Terminal output:
{: .fs-3 }
![](/assets/images/sql/step3.png)
<br>
<br>
<br>
### 📄 Task 2: Retrieve login attempts on specific dates
A suspicious event occurred on 2022-05-09. To investigate this, I review all login attempts which occurred on this day and the day before:
```sql
SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';
```

{: .note2 }
WHERE and the OR operator limits the data from the login_date column to either 2022-05-09 or 2022-05-08. With the OR operator, either condition can be met.

Terminal output:
{: .fs-3 }
![](/assets/images/sql/step4.png)
<br>
<br>
<br>
### 📄 Task 3: Retrieve login attempts outside of Mexico
There’s been suspicious activity with login attempts, but the team has determined that this activity didn't originate in Mexico. I need to  investigate login attempts that occurred outside of Mexico. To do this, I used the following command:
```sql
SELECT *
From log_in_attempts
WHERE NOT country LIKE 'MEX%';
```

{: .note2 }
> In the country column of the queried table, Mexico is represented by either "MEX" or "MEXICO." I need to filter for a pattern to obtain the data I need. 
>
> In the portion of the command "LIKE 'MEX%'," the LIKE operator allows me to filter by a pattern while % is a wildcard that substitutes for any number of characters. NOT negates the condition where the pattern matched must start with "MEX," so the output excludes all country data related to Mexico.

Terminal output:
{: .fs-3 }
![](/assets/images/sql/step5.png)
<br>
<br>
<br>
### 📄 Task 4: Retrieve employees in Marketing
My team wants to perform security updates on specific employee machines in the Marketing department. These employees must also be from the East building. I will need to query the employees table. 
```sql
SELECT *
FROM employees
WHERE department = 'Marketing' AND office LIKE 'East%';
```

{: .note2 }
The AND operator requires that both conditions must be true. Because of this, only data on employees who work in the Marketing department and are located in the all areas of the East building are returned.

Terminal output:
{: .fs-3 }
![](/assets/images/sql/step6.png)
<br>
<br>
<br>
### 📄 Task 5: Retrieve employees in Finance or Sales
My team needs to perform a security update on machines for employees in the Sales and Finance departments. I query the "employees" table in the following way:
```sql
SELECT *
FROM employees
WHERE department = 'Sales' OR department = 'Finance';
```

{: .note2 }
By using WHERE and OR, data on employees from the Sales department and employees from the Finance department is returned.

Terminal output:
{: .fs-3 }
![](/assets/images/sql/step7.png)
<br>
<br>
<br>
### 📄 Task 7: Retrieve all employees not in IT
My team needs to make one more update to employee machines. The employees who are in the Information Technology department already had this update, but employees in all other departments need it.
```sql
SELECT *
FROM employees
WHERE NOT department = 'Information Technology';
```

{: .note2 }
The NOT operator negates a condition. This means that SQL returns all records that don’t match the condition specified in the query. Data on employees who are not from the Information Technology department are outputted to the terminal.

Terminal output:
{: .fs-3 }
![](/assets/images/sql/step8.png)
<br>
<br>
<br>
### Summary

Using SQL, I was able to query the relevant databases to investigate suspicious login attempts and identify which employee machines need critical updates. Using the SELECT and FROM commands helped query the correct databases. Filtering using the WHERE keyword and the appropriate operators such as AND, OR, and NOT helped me narrow down the data and made my investigations much more efficient.

---

<a href="#top" id="back-to-top">Back to top</a>