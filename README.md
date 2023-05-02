# SQLExercises

emp_id | emp_name | job_name | manager_id | hire_date | salary | commission | dep_id
--------+----------+-----------+------------+------------+---------+------------+--------
68319 | KAYLING | PRESIDENT | | 1991-11-18 | 6000.00 | | 1001
66928 | BLAZE | MANAGER | 68319 | 1991-05-01 | 2750.00 | | 3001
67832 | CLARE | MANAGER | 68319 | 1991-06-09 | 2550.00 | | 1001
65646 | JONAS | MANAGER | 68319 | 1991-04-02 | 2957.00 | | 2001
67858 | SCARLET | ANALYST | 65646 | 1997-04-19 | 3100.00 | | 2001
69062 | FRANK | ANALYST | 65646 | 1991-12-03 | 3100.00 | | 2001
63679 | SANDRINE | CLERK | 69062 | 1990-12-18 | 900.00 | | 2001
64989 | ADELYN | SALESMAN | 66928 | 1991-02-20 | 1700.00 | 400.00 | 3001
65271 | WADE | SALESMAN | 66928 | 1991-02-22 | 1350.00 | 600.00 | 3001
66564 | MADDEN | SALESMAN | 66928 | 1991-09-28 | 1350.00 | 1500.00 | 3001
68454 | TUCKER | SALESMAN | 66928 | 1991-09-08 | 1600.00 | 0.00 | 3001
68736 | ADNRES | CLERK | 67858 | 1997-05-23 | 1200.00 | | 2001
69000 | JULIUS | CLERK | 66928 | 1991-12-03 | 1050.00 | | 3001
69324 | MARKER | CLERK | 67832 | 1992-01-23 | 1400.00 | | 1001

#### From the following table, write a SQL query to find the salaries of all employees. Return salary.

- SELECT employees.salary FROM employees

#### From the following table, write a SQL query to find the unique designations of the employees. Return job name.

- SELECT DISTINCT employees.job_name from employees
  - DISTINCT use for unique find

#### From the following table, write a SQL query to list the employees’ name, increased their salary by 15%, and expressed as number of Dollars.

- SELECT employees.emp_name to_char(1.15\*salary,'$99,999') AS "Salary" FROM employees

#### Write a query in SQL to produce the output of employees as follows. JONAS(manager).

- SELECT employees.emp_name || '('|| lower(job_name) ||')' AS "Employee" from employees

#### From the following table, write a SQL query to find those employees with hire date in the format like February 22, 1991. Return employee ID, employee name, salary, hire date.

- SELECT
  employees.emp_id,
  employees.emp_name,
  employees.salary,
  to_char(hire_date,'MONTH DD,YYYY')
  FROM employees

#### From the following table, write a SQL query to find the employee ID, salary, and commission of all the employees.

- select emp_id,salary,commission from employees

#### From the following table, write a SQL query to find the unique department with jobs. Return department ID, Job name.

- SELECT DISTINCT dep_id,
  job_name
  FROM employees ;

#### From the following table, write a SQL query to find those employees who do not belong to the department 2001. Return complete information about the employees

- select \* from employees where employees.dep_id != 2001

#### write a SQL query to find those employees who joined before 1991. Return complete information about the employees.

- select \* from employees where employees.hire_date<('1991-1-1')

#### From the following table, write a SQL query to calculate the average salary of employees who work as analysts. Return average salary

- select avg(salary) from employees where employees.job_name = 'ANALYST'

#### From the following table, write a SQL query to find the details of the employee ‘BLAZE’.

- select \* from employees where employees.emp_name='BLAZE'

#### From the following table, write a SQL query to identify employees whose commissions exceed their salaries. Return complete information about the employees.

- select \* from employees where employees.commission>employees.salary

#### From the following table, write a SQL query to identify those employees whose salaries exceed 3000 after receiving a 25% salary increase. Return complete information about the employees.

- select * from employees where (1.25*employees.salary)>3000

#### From the following table, write a SQL query to find the names of the employees whose length is six. Return employee name.

- select emp_name from employees where length(employees.emp_name)=6

#### From the following table, write a SQL query to find out which employees joined in the month of January. Return complete information about the employees.

- select \* from employees where to_char(hire_date,'mon')='jan'

#### From the following table, write a SQL query to separate the names of employees and their managers by the string 'works for'.

- select e.emp_name || 'works for' || m.emp_name from employees e,employees m
  where e.manager_id=m.emp_id

#### From the following table, write a SQL query to find those employees whose designation is ‘CLERK’. Return complete information about the employees.

- select \* from employees where employees.job_name ='CLERK'

#### From the following table, write a SQL query to find those employees who joined in any month, but the name of the month contain the character ‘A’ in second position. Return complete information about the employees

- select \* from employees where to_char(hire_date,'MON') like '\_A%'

#### From the following table, write a SQL query to find those employees who joined in any month, but the month name contain the character ‘A’. Return complete information about the employees.

- select \* from employees where to_char(hire_date,'MON') like '%A%

#### From the following table, write a SQL query to find those employees whose name ends with 'S' and six characters long. Return complete information about the employees.

- select \* from employees where emp_name like '%S' and length(emp_name)=6

#### From the following table, write a SQL query to find those employees whose names contain the letter 'A’. Return complete information about the employees

- select \* from employees where emp_name like '%A%'

#### From the following table, write a SQL query to find those employees whose ID not start with the digit 68. Return employee ID, employee ID using trim function.

- select emp_id,trim(to_char(emp_id,'9999'))
  from employees where trim(to_char(emp_id,'9999')) NOT LIKE '68%'

#### From the following table, write a SQL query to find those employees who joined in 90's. Return complete information about the employees

- select \* from employees where to_char(hire_date,'YY') LIKE '9%'

#### From the following table, write a SQL query to identify those employees whose names begin with 'A' and are six characters long. Return employee name

- select emp_name from employees where emp_name LIKE 'A%' AND length(emp_name)=6

#### From the following table, write a SQL query to find number of employees and average salary. Group the result set on department id and job name. Return number of employees, average salary, department ID, and job name.

select count(\*), avg(salary),dep_id,job_name from employees group by dep_id,job_name

#### From the following table, write a SQL query to check whether the employees ID are unique or not. Return employee id, number of employees.

- SELECT emp_id,
  count(\*)
  FROM employees
  GROUP BY emp_id;
