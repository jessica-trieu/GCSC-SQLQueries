# Google Cybersecurity Certificate Project: Apply Filters to SQL Queries

## Project Description

The purpose of this project is to demonstrate how to filter data when using SQL, specifically the use of ``AND``, ``OR``, and ``NOT``.

**Scenario**: Recently, some potential security issues have been discovered that involve login attempts and employee machines. I investigated the issues using SQL filters to retrieve records from different datasets, specifically from the ``employees`` and ``log_in_attempts`` tables.

## Retrieve after hours failed login attempts
Since the potential security incident occurred after 6pm, I needed to investigate the failed login attempts after that time.

To create this query, I selected all (the asterisks (``*``) means to include all columns) data from the ``log_in_attempts`` table using the ``FROM`` clause. Then I filtered the results using the ``WHERE`` clause and ``AND`` operator to set my conditions where the login time was after 6pm (``login_time > ‘18:00’``) and the login attempts failed (``success = FALSE``). 

![image](https://github.com/user-attachments/assets/bcd3ff28-9e56-4db9-94d1-4af0d0b8abfa)

From the results, there were 19 attempted and failed logins after 6pm. 

## Retrieve login attempts on specific dates
A suspicious event occurred on 2022-05-09. To investigate this event, I reviewed all login attempts which occurred on 2022-05-08 and 2022-05-09.  

I selected all data from the ``log_in_attempts`` table. Then I filtered the data using the ``WHERE`` clause so that the data I pulled were from the dates 2022-05-08 and 2022-05-09 (``login_dates = 2022-05-08`` and ``login_dates = 2022-05-09``). Using the ``OR`` operator allows me to include both dates in the results.

![image](https://github.com/user-attachments/assets/3bcff51a-661a-4a20-a7d6-2a451a8de3ce)

From the results, there were 75 logins from 2022-05-08 to 2022-05-09. 

## Retrieve login attempts outside of a location

There’s been suspicious activity with login attempts, but the team has determined that this activity didn't originate in Mexico. So when investigating, I needed to filter out countries that are not Mexico.

To start, I selected all the data from the ``log_in_attempts`` table using the ``FROM`` clause. Then I use to the ``WHERE`` clause to set my conditions for the ``country`` column. In the database, Mexico is entered as ``Mex`` or ``Mexico``, so I will use ``NOT``, ``LIKE``,  and ``‘Mex%’`` to exclude the results in the same row as Mexico. The percentage sign (``%``) is a placeholder for any number of unspecified characters when used with ``LIKE``. 

![image](https://github.com/user-attachments/assets/4d84a937-6477-4565-bc71-d09397f42594)

The results show that there were 144 logins outside of Mexico. 

## Retrieve employees in Marketing

The team wants to perform security updates on specific employee machines in the Marketing department of the East buildings. 

To start my query, I selected all data from the ``employees`` table. Then I filtered the data using the ``WHERE`` clause so it would include the conditions that the employee machines belong to employees in the marketing department (``department = ‘Marketing’``) and that the offices were in in the East building (``office LIKE ‘East%``). To include all East building offices, I used ``LIKE`` and ``‘East%’`` since the offices have different room numbers. I also used the ``AND`` operator so that the output displays results where _both_ conditions are met. 

![image](https://github.com/user-attachments/assets/dc3e0a70-9367-4f9d-bef3-4499e10313d8)

The results show that there are 7 employee machines that need to be updated.

## Retrieve employees in Finance or Sales

The team needs to perform a different security update on machines for employees in the Sales and Finance departments.

To start my query, I selected all data from the ``employees table``. I then filtered the data so it would include the conditions that the employee machines belong to employees in the Finance department (``department =  ‘Finance’``) or in the Sales department (``department = ‘Sales'``). Using the ``OR`` operator would have the results include either Finance or Sales employees.

![image](https://github.com/user-attachments/assets/f12a12de-5022-48d2-b8e2-bd1144ffd435)

The results show that there are 71 employees in Finance or Sales that need the new security update.

## Retrieve all employees not in IT

The team needs to make one more update. The employees who are in the Information Technology (IT) already had this update, but employees in all other departments need it.

I start my query by selecting all data from the ``employees`` table. I then set the conditions using the ``WHERE`` clause. To exclude employees from the IT department (``department = ‘Information Technology’``), I used the ``NOT`` operator when specifying what the query should pull from the department column.   

![image](https://github.com/user-attachments/assets/297c81f5-4d77-4e9e-a248-79fbfcdf6eac)

The results show that there 161 employees not in the IT department and need the new update.

## Summary

By using the ``WHERE`` clause and the operators  ``AND``,``OR``, and ``NOT`` in SQL, I was able to filter data and identify which employees had made login attempts on certain dates/times and certain countries, as well as employees from different offices and departments. I also used ``LIKE`` and the percentage sign (`%`) wildcard to filter for patterns. The tables I pulled the data was from ``employees`` and ``log_in_attempts``.



