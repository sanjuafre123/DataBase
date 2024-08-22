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

## Table in App Inspection

## Database Helper class
```bash

import 'package:path/path.dart';
import 'package:sqflite/sqflite.dart';

class DatabaseHelper {
  static DatabaseHelper databaseHelper = DatabaseHelper._();

  DatabaseHelper._();

  static const String databaseName = 'notes.db';
  static const String tableName = 'notes';

  Database? _database;

  Future<Database?> get database async => _database ?? await initDatabase();

  Future<Database?> initDatabase() async {
    final path = await getDatabasesPath();
    final dbPath = join(path, databaseName);
    return await openDatabase(
      dbPath,
      version: 1,
      onCreate: (db, version) {
        String sql = '''
      CREATE TABLE $tableName (
      id INTEGER PRIMARY KEY AUTOINCREMENT,
      amount INTEGER NOT NULL,
      description TEXT NOT NULL,
      category TEXT
      )
      ''';
        db.execute(sql);
      },
    );
  }

  Future<int> insertData() async {
    final db = await database;
    String sql = '''
    INSERT INTO $tableName (amount, description)
    VALUES (750, 'Travel reimbursement');
    ''';
    final result = await db!.rawInsert(sql);
    return result;
  }

  Future<int> deleteData(int id) async {
    final db = await database;
    String sql = '''
    DELETE FROM $tableName WHERE id = $id
    ''';
    final result = await db!.rawDelete(sql);
    return result;
  }
}

```

## Controller
```bash

import 'package:get/get.dart';

import '../Helper/helper.dart';

class BudgetController extends GetxController{

  @override
  void onInit(){
    super.onInit();
    initDb();
  }

  Future initDb() async{
    await DatabaseHelper .databaseHelper.database;
  }

  Future insertRecord() async{
    await DatabaseHelper.databaseHelper.insertData();
  }
  Future deleteRecord(int id) async{
    await DatabaseHelper.databaseHelper.deleteData(id);
  }
}

```

## Database inspector

<img src="https://github.com/user-attachments/assets/7e8f70e7-076d-4b02-a057-16eabd0ebf46">




