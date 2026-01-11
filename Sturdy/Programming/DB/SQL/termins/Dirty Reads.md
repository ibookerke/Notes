Common problem for Read Uncommitted [[Isolation levels]]
A transaction reads uncommitted changes from another transaction, which might later be rolled back.

**Example**:
    - Transaction A modifies a record but hasn’t committed it yet.
    - Transaction B reads this uncommitted data, even though Transaction A might roll it back later.