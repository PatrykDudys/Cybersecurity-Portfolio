# SQL Security Analysis Project

## Project Description
In this project, I utilized SQL to investigate potential security issues within an organization. The goal was to ensure system safety, thoroughly examine potential security threats, and verify that all employee computers were updated as required. 

The project demonstrates how SQL queries with filters and conditions can be applied to identify suspicious activity and manage employee devices effectively.

---

## SQL Queries Overview

| Task | Purpose | Example SQL Query |
|------|---------|-----------------|
| Retrieve After-Hours Failed Login Attempts | Identify failed login attempts after business hours (18:00) for suspicious activity | ```sql SELECT * FROM login_attempts WHERE login_time > '18:00:00' AND success = 0; ``` |
| Retrieve Login Attempts on Specific Dates | Investigate login activity on or before a reported suspicious event (2022-05-09) | ```sql SELECT * FROM login_attempts WHERE login_date IN ('2022-05-08', '2022-05-09'); ``` |
| Retrieve Login Attempts Outside of Mexico | Detect login attempts originating outside Mexico | ```sql SELECT * FROM login_attempts WHERE country NOT LIKE '%Mexico%'; ``` |
| Retrieve Employees in Marketing | Identify Marketing department employees in the East building for updates | ```sql SELECT * FROM employees WHERE department = 'Marketing' AND building = 'East'; ``` |
| Retrieve Employees in Finance or Sales | Filter employees in Finance or Sales for specific security updates | ```sql SELECT * FROM employees WHERE department IN ('Finance', 'Sales'); ``` |
| Retrieve All Employees Not in IT | Prepare security updates for employees outside the IT department | ```sql SELECT * FROM employees WHERE department <> 'IT'; ``` |

---

## Summary
This project demonstrates the use of SQL filters and logical operators to:  

- Investigate failed login attempts  
- Identify suspicious activity by date or location  
- Manage employee updates based on department  
- Utilize pattern matching for flexible data filtering  

Two main tables were used: `login_attempts` and `employees`. Each query shows how logical conditions can effectively isolate relevant information for cybersecurity and system management purposes.
