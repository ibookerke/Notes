A transaction reads the same data twice and gets different results because another transaction modified and committed it in the meantime

**Example**:
    - Transaction A reads a value (e.g., account balance = $100).
    - Transaction B updates and commits the balance to $200.
    - When Transaction A reads the balance again, it sees $200.


