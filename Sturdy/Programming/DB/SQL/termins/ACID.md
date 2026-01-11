ACID is an acronym that refers to the set of 4 key properties that define a transaction: **Atomicity, Consistency, Isolation, and Durability**.

Atomicity - Think of a transaction as a single, all-or-nothing action. Either every step in the transaction happens successfully, or nothing happens at all.

Consistency - The database should always be in a valid state before and after a transaction

Isolation - Transactions should not interfere with each other, even if they happen at the same time. More About Isolation in [[Isolation levels]]


Durability - Once a transaction is successfully completed, the changes it made are permanent, even if there’s a power failure or crash

