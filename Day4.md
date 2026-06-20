// 19/06/2026

use school_db;
CREATE table emp(
emp_id int primary KEY auto_increment,                                                                  -- Primary KEY -> Constraints, auto_increment -> Property 
first_name varchar(30) NOT NULL,                                                                        -- NOT NULL -> Constraints
last_name varchar(30) NOT NULL,                                                                         -- NOT NULL -> Constraints
hire_date date default (current_date()),                                                                -- default -> Constraints
email varchar(50) unique,                                                                               -- unique -> Constraints
salary decimal(10,2) check (salary > 0.0),
emp_status enum('active', 'on leave', 'terminated') default 'active',
created_at timestamp default current_timestamp
);



// 20/ 06/2026
//Master SQL SELECT

insert INTO emp (first_name, last_name, email,salary) values
('Sampa', 'Nayak', 'sampa@gmail.com', 23334),
('Arpita', 'Nayak', 'arpita@gmail.com', 34000),
('Rudra', 'Verma', 'rudra98@gmail.com', 50000);
SELECT * FROM emp;
SELECT first_name, last_name from emp; 
SELECT first_name as 'First_Name', last_name from emp;
SELECT * FROM emp where emp_status = 'active';
SELECT * FROM emp order by salary desc;
SELECT * FROM emp limit 2;
SELECT * FROM emp order by salary desc limit 1;  -- Find highest salary
Select distinct email from emp;   -- Duplicate not allowed
SELECT salary*1.1 as 'Updated salary' FROM emp;  -- SALARY INCREASE
SELECT concat(first_name, ' ',last_name) as 'Full name', YEAR(hire_date), Round(salary,1) from emp where salary > 30000;
SELECT * from emp where salary > avg(salary);
SELECT COUNT(*), emp_status FROM emp GROUP BY emp_status;
SELECT 2+2;
SELECT now() as 'time';
SELECT LENGTH('SAMPA');