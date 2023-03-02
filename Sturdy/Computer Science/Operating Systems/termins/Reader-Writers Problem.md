For instance:
- A database is to be shared with several concurrent processes.
- Some of these processes may only want to read the database, whereas others may want to update (i.e., read and write) the database.
- We differentiate these processes as Readers to the former and to the latter as Writers.
- If two readers are accessing the database simultaneously, no adverse affects will result.
- However, if a writer and some other thread (either a reader or a writer) access the database simultaneously, chaos may occur.
- To ensure that these difficulties do not arise, we require that the writers have exclusive access to the shared database.
- This synchronization problem is referred as readers-writers problem.

