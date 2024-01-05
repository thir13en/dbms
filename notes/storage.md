# Storage

## Rows, Tables, Pages

### 1. Tables
A table in a database is a collection of related data held in a structured format within a database. It consists of columns and rows.
- **Columns**: Each column in a table represents a particular type of data. For example, a table of customer information might include columns for customer ID, name, address, and phone number. Each column has a specific data type, such as integer, date, text, etc.
- **Rows**: A row in a table represents a single record or data item. Each row in the customer information table would contain the data for one customer - one ID, one name, one address, and one phone number.

Tables are the most common and easily understood form of data storage in relational databases. They can be related to each other through keys (primary keys and foreign keys), allowing for the organization and retrieval of complex data in a relational manner.

### 2. Rows
A row, sometimes referred to as a record, is a single, implicitly structured data item in a table. In simple terms, it's one "line" of data.
- **Data Organization**: A row combines data for each column into a single unit. For example, in a customer table, one row would contain all the information about a single customer.
- **Uniqueness**: Each row can be uniquely identified by a primary key. The primary key is a column or a set of columns whose values uniquely identify every row in the table.

### 3. Pages

Pages relate to how data is stored at the database system's physical level, particularly in disk-based databases.
- **Storage Units**: A page is the basic unit of data storage in a database. Databases store and retrieve data in pages. 
- **Size**: The size of a page is typically a few kilobytes and is fixed for a given database system. For example, SQL Server uses 8 KB pages, while PostgreSQL uses pages of size 4 KB or 8 KB depending on the build.
- **Data Organization**: A page can store one or more rows, depending on the size of the rows. Each page contains data from a single table, and the rows are stored sequentially in the page.
- **Efficiency**: By using pages, the database system can efficiently read and write data to disk. When a query is run, the database retrieves data by reading the relevant pages into memory, rather than reading individual rows or entire tables.