# ACID

Set of properties that ensure the reliability and consistency of transactions in a database system. These properties are fundamental for maintaining the integrity of data in a database, especially in the context of transactions. ACID stands for **Atomicity**, **Consistency**, **Isolation**, and **Durability**.


    Atomicity:
        Definition: Atomicity ensures that a transaction is treated as a single, indivisible unit of work. Either all the changes made by the transaction are committed to the database, or none of them are.
        Example: In a banking application, when transferring money from one account to another, atomicity ensures that both the debit from one account and the credit to the other account occur as a single, atomic operation.

    Consistency:
        Definition: Consistency ensures that a transaction brings the database from one valid state to another. It preserves the integrity of the database schema and enforces any defined rules or constraints.
        Example: If a database enforces a rule that all email addresses must be unique, consistency ensures that a transaction that attempts to insert a duplicate email address is rolled back, preventing an inconsistent state.

    Isolation:
        Definition: Isolation ensures that the execution of one transaction is isolated from the execution of other transactions. Transactions appear to be executed in a sequential order, even if they are executed concurrently.
        Example: If two transactions are modifying the same data simultaneously, isolation ensures that each transaction is unaware of the other until it is committed. This prevents interference and maintains data integrity.

    Durability:
        Definition: Durability guarantees that once a transaction is committed, its effects are permanent and survive any subsequent failures, such as power outages or system crashes.
        Example: After a user makes changes to a database and receives a confirmation, durability ensures that even if the system crashes immediately afterward, the changes will be preserved when the system is restored.

## What is a transaction?
A transaction is a collection of queries that are treated as a single unit of work. Always begins with the keywork `BEGIN` and it ends with the keyword `COMMIT`. When things do not go right, we end up doing a `ROLLBACK`. You can have `readonly` transactions.

## Atomicity
Guarantees that operations (transctions etc) are carried in an unary manner and only persisted/commited when fully completed.

## Isolation

Isolation in database systems refers to the ability to concurrently process multiple transactions in a way that each transaction is isolated from others. This means that the operations in one transaction are hidden from other transactions until the transaction is completed. Isolation ensures that concurrent execution of transactions leaves the database in the same state as if the transactions were executed sequentially. This is crucial for maintaining data integrity.
Key Points about Isolation:

    Concurrent Transactions: Databases often handle many transactions at the same time. Without proper isolation, transactions might interfere with each other.

    Visibility of Changes: The changes made in a transaction are not visible to other transactions until the transaction is committed. This prevents other transactions from reading intermediate, potentially inconsistent data.

    Preventing Interference: Isolation ensures that the transactions do not interfere with each other even while accessing the same data. For example, if two transactions are trying to update the same row in a table, one transaction will have to wait until the other completes.

    Isolation Levels: There are different levels of isolation that offer a trade-off between performance and the degree of isolation. These include Read Uncommitted, Read Committed, Repeatable Read, and Serializable. Each level provides different handling of concurrent transactions and has different impacts on phenomena like Dirty Reads, Nonrepeatable Reads, and Phantom Reads.
        Read Uncommitted: The lowest level where transactions may read changes made by other transactions before they are committed. This can lead to Dirty Reads.
        Read Committed: Ensures that any data read is committed at the moment it is read. This prevents Dirty Reads but not Nonrepeatable Reads.
        Repeatable Read: Ensures that if a transaction reads data, it will read the same data again if queried before the transaction completes. This prevents Dirty Reads and Nonrepeatable Reads but not Phantom Reads.
        Serializable: The highest level of isolation. Transactions are executed with full isolation; it's as if transactions are executed one after the other.

Importance:

    Consistency: Isolation helps maintain database consistency by ensuring that transactions don't make conflicting changes.
    Error Handling: It allows for error handling in a multi-user environment, ensuring that faulty transactions don't affect others.
    Data Integrity: It protects the integrity of data by ensuring that transactions can't interfere with each other.

# Dirty Reads, Nonrepeatable Reads, and Phantom Reads
Phenomena related to transactional operations in a database, particularly concerning the level of isolation. They represent different kinds of anomalies that can occur when transactions are executed concurrently without sufficient isolation.

1. Dirty Reads
A dirty read occurs when a transaction reads data that has been written by another transaction that has not yet been committed. Since the second transaction hasn't been committed, there's a chance it might be rolled back, meaning the read data could be inconsistent or invalid.

    Example: Imagine Transaction 1 updates a record but hasn't committed the changes. Transaction 2 reads the same record before Transaction 1 commits it. If Transaction 1 is rolled back, Transaction 2 will have read data that never actually existed in the database.

2. Nonrepeatable Reads
A nonrepeatable read happens when a transaction reads the same row twice and gets different data each time. This occurs when another transaction modifies or commits data between the two reads of the original transaction.

    Example: Transaction 1 reads a record. Transaction 2 then updates or deletes that record and commits the change. If Transaction 1 attempts to read the same record again, it finds different data (or finds that the record is missing), leading to inconsistency.

3. Phantom Reads
A phantom read is a situation where a transaction re-executes a query returning a set of rows that satisfy a certain condition and finds that another transaction has added or removed rows that satisfy the condition, thus changing the result set of the original query.

    Example: Transaction 1 reads a set of rows that meet a specific condition. Meanwhile, Transaction 2 adds or removes rows that alter the set of rows meeting the condition. When Transaction 1 re-runs the same query, it gets a different set of rows, hence the "phantom" data.

Isolation Levels and These Phenomena

The isolation levels in SQL databases (Read Uncommitted, Read Committed, Repeatable Read, and Serializable) are designed to prevent these phenomena:

    Read Uncommitted: This level doesn't prevent any of the three phenomena. It allows dirty reads.
    Read Committed: Prevents dirty reads but not nonrepeatable reads or phantom reads.
    Repeatable Read: Prevents dirty and nonrepeatable reads but may not prevent phantom reads.
    Snapshot: is a method used to provide a consistent view of data for each transaction, preventing it from seeing partial changes made by other concurrent transactions.
    Serializable: Prevents all three phenomena. This is the strictest level, ensuring full isolation but at the cost of reduced concurrency and potential performance impacts.

Understanding these concepts is crucial for database designers and administrators to ensure data integrity and consistency, especially in systems with high levels of concurrency and transactional operations.