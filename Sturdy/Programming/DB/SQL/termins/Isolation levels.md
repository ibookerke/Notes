The implementation of isolation may differ, but there are 4 common legitimate isolation levels:

1. **Read Uncommitted**:
    
    - **Description**: The lowest isolation level. A transaction can read data that has been modified but not yet committed by other transactions.
    - **Problems**:
        - **[[Dirty Reads]]**
    - **Use Case**: Rarely used, typically for scenarios where performance is critical, and data accuracy is less important.

---

2. **Read Committed** (Default for most databases):
    
    - **Description**: A transaction only reads committed data. Uncommitted changes from other transactions are invisible.
    - **Problems**:
        - **[[Non-Repeatable Reads]]**
    - **Use Case**: Ensures you don't see dirty data while maintaining good performance.

---

3. **Repeatable Read**:
    
    - **Description**: Ensures that if a transaction reads the same data multiple times, the results are always consistent, even if other transactions modify the data in the meantime.
    - **Problems**:
        - **[[Phantom Reads]]**
    - **Use Case**: For scenarios where consistent results from multiple reads of the same data are important.

---

4. **Serializable**:
    
    - **Description**: The strictest isolation level. Transactions are executed as if they were run sequentially, one after the other, even if they happen simultaneously.
    - **Problems**: None in terms of consistency, but it can significantly reduce performance due to high locking and blocking.
    - **Use Case**: Used in scenarios requiring the highest level of data accuracy and consistency, such as financial systems.
    
    **Example**:
    - Transaction A reads all records where `age > 18`.
    - Transaction B tries to insert a record with `age = 25` but must wait until Transaction A finishes to ensure no conflicts.