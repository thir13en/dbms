# SQL

### What is SQL?
SQL is a standard programming language specifically designed for managing and manipulating data held in a relational database management system (RDBMS). It is used for tasks such as querying data, updating data, creating and modifying schemas, and managing database objects.

### Starting with SQL
1. **SELECT**: The most fundamental SQL command, used to fetch data from a table.
2. **INSERT**: Used to insert data into a table.
3. **UPDATE**: Used to modify existing data in a table.
4. **DELETE**: Used to remove data from a table.
5. **CREATE TABLE**, **ALTER TABLE**, **DROP TABLE**: Used to create, modify, and delete tables, respectively.

### First SQL Query
A simple SQL query looks like this:

```sql
SELECT * FROM Employees;
```
Which refers to
```sql
SELECT [...column_name1,column_name2...column_nameN] FROM table_name;
```
It is important to note that it goes from more specific to more generic <-------------

This command selects all columns (`*`) from the `Employees` table.