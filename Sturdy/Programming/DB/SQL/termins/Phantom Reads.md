A transaction may see new rows added by another transaction when re-executing a query


**Example**:
    - Transaction A reads all records where `age > 18`.
    - Transaction B inserts a new record with `age = 25` and commits.
    - Transaction A reads again and sees the new record (phantom read).