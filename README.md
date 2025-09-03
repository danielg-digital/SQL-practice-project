# SQL Log & Employee Security Analysis

## Objective
This project simulates the discovery of potential security issues involving login attempts and employee machine updates. Using SQL queries, I identified suspicious login activity and filtered employee data to assist with targeted security updates.

### Skills Learned

-Practical use of SQL for log analysis and data filtering

-Ability to identify suspicious login activity (after hours, by date, and by country)

-Experience using SQL filters (AND, OR, NOT, LIKE) to refine results

-Understanding how query results can support incident response and patch management

-Improved problem-solving and analytical skills in cybersecurity scenarios

### Tools Used

-SQL (for queries and filtering data)

-Simulated employee and login datasets (CSV/DB tables)

-MySQL

# Steps
## 1.Retrieve after-hours failed login attempts

SELECT *
FROM log_in_attempts
WHERE login_time >= '18:00' AND success = 'FALSE';

<img width="808" height="670" alt="Screenshot 2025-09-02 204255" src="https://github.com/user-attachments/assets/c8ae9eba-1847-47a5-b272-e63fe8192f7a" />


Identified failed login events occurring after business hours. A suspicious event was noted on 2022-05-09.


## 2. Retrieve login attempts on specific dates

SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';

<img width="710" height="879" alt="Screenshot 2025-09-02 204450" src="https://github.com/user-attachments/assets/031e2cd4-91ad-4585-8c3c-59fd9913969e" />

Reviewed all login attempts surrounding the suspicious event.

## 3. Retrieve login attempts outside of Mexico

SELECT *
FROM log_in_attempts
WHERE country NOT LIKE 'Mex%';

<img width="708" height="882" alt="Screenshot 2025-09-02 204607" src="https://github.com/user-attachments/assets/7f5fc6a2-eca5-43cd-8ffa-792924d54835" />

Filtered logins to exclude Mexico, isolating attempts from other regions.


## 4. Retrieve Marketing employees in East office

SELECT *
FROM employees
WHERE department = 'Marketing' AND office LIKE 'East%';

<img width="624" height="257" alt="Screenshot 2025-09-02 205511" src="https://github.com/user-attachments/assets/8ee9cf9e-39d8-498c-aa2d-ef3d066651b8" />

Narrowed down employees in the Marketing department, East office, for security updates.


## 5. Retrieve employees in Finance or Sales

SELECT *
FROM employees
WHERE department = 'Finance' OR department = 'Sales';

<img width="559" height="824" alt="Screenshot 2025-09-02 205619" src="https://github.com/user-attachments/assets/a660d65a-60b5-4b64-b147-38725d8eef15" />

Isolated employees in Finance or Sales departments for targeted patching.


## 6. Retrieve all employees not in IT

SELECT *
FROM employees
WHERE department <> 'Information Technology';

<img width="596" height="784" alt="Screenshot 2025-09-02 210039" src="https://github.com/user-attachments/assets/eb632ca8-db7b-4593-8a6a-65fe338a51a4" />

Excluded IT staff from updates, focusing on end-user machines.



## Summary

Through SQL analysis, suspicious login activity was identified, particularly failed after-hours login attempts on 2022-05-09. Further investigation into logins from May 8th and 9th confirmed unusual patterns, excluding activity from Mexico. Targeted employee groups were then identified for security updates, including Marketing (East office), Finance, and Sales. Finally, IT employees were excluded from patching since their systems were already secured.

This exercise highlights how SQL can be used to analyze security logs and support IT teams in prioritizing response efforts.



