# Ex. No: 5 Creating Triggers using PL/SQL

### AIM: To create a Trigger using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
3. Create a trigger named as log_salary-update.
4. Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.
5. End the trigger.
6. Update the salary of an employee in employee table.
7. Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.
8. Display the employee table, salary_log table.

### Program:
### Create employee table
```
CREATE TABLE employee (empid INT,empname VARCHAR(10),dept VARCHAR(10),salary float);
```

### Create salary_log table
```
CREATE TABLE salary_log ( log_id INT AUTO_INCREMENT PRIMARY KEY,empid INT,empname VARCHAR(10),old_salary float,new_salary float,update_date DATE);
```

### PLSQL Trigger code
```
DELIMITER //

CREATE TRIGGER log_salary_update
AFTER UPDATE ON employee
FOR EACH ROW
BEGIN
    IF OLD.salary <> NEW.salary THEN
        INSERT INTO salary_log (empid, empname, old_salary, new_salary, update_date)
        VALUES (NEW.empid, NEW.empname, OLD.salary, NEW.salary, NOW());
    END IF;
END //

DELIMITER ;

SELECT * FROM employee;

SELECT * FROM salary_log;
```
### Output:
![image](https://github.com/Meetha22003992/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/119401038/d04ca3f7-d710-47c7-9ee5-2a8d75d44175)

![image](https://github.com/Meetha22003992/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/119401038/e57b43d3-226d-4f92-a94d-65c480f7cdfb)


### Result:
Thus triggered code is created successfully
