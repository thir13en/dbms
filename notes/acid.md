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