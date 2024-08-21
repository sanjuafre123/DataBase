# DataBase

This repository contains SQL scripts for managing an `employees` table. The table includes columns for name, role, salary, age, and phone number. Below are the details of the table structure and various SQL operations performed.

- ## To create table
```bash
CREATE TABLE "employees" (

	"Id"	INTEGER,
	"Name"	TEXT NOT NULL,
	"Role"	TEXT NOT NULL,
	"Salary"	INTEGER NOT NULL,
	"Age"	INTEGER NOT NULL,
	"Phone"	BLOB NOT NULL,
	PRIMARY KEY("Id" AUTOINCREMENT)

)
```

- ## Data Insertion

Inserting data into the `employees` table:

```bash

INSERT INTO employees (Name,Role,Salary,Age,Phone) VALUES ("John","Engineer",90000,28,5551234567);
INSERT INTO employees (Name,Role,Salary,Age,Phone) VALUES ("Emily","Manager",105000,26,5553456789);
INSERT INTO employees (Name,Role,Salary,Age,Phone) VALUES ("Michael","Data Analyst",75000,26,5552345678);
INSERT INTO employees (Name,Role,Salary,Age,Phone) VALUES ("Sarah","UX Designer",85000,30,5554567890);
INSERT INTO employees (Name,Role,Salary,Age,Phone) VALUES ("David","HR Specialist",70000,28,5555678901);

```

### Selecting all data from the `employees` table:

```bash
SELECT * FROM employees;
```
### Selecting specific columns:

```bash
SELECT Name From employees;
SELECT Salary From employees;
```

### Filtering data based on conditions:

```bash

SELECT * FROM employees WHERE Role = "Engineer";
SELECT * FROM employees WHERE Name Like 'J%';
SELECT * FROM employees WHERE (Age > 25 AND Salary > 95000);

```
- ## Data Update

### Updating data in the `employees` table:

```bash

UPDATE employees SET Salary = 60000 WHERE Id = 3;
UPDATE employees SET Phone = 9726548975 WHERE Id = 1;

```

- ## Data Delete

### Deleting data from the `employees` table:

```bash

DELETE FROM employees WHERE Id = 5;
DELETE FROM employees WHERE Age > 30;

```

- ## Table :

![image](https://github.com/user-attachments/assets/d6639f53-fcae-4a3c-a7f7-5a2daf9a7ef8)






