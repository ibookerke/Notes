![[Pasted image 20221108164348.png]]


## Data Independence
- **Physical data independence**: The ability to change the physical schema without affecting conceptual / logical schema.
- **Logical data independence**: The ability to change the conceptual/logical structure without affecting existing external views

**Data structures** - deal with data in main memory
**File Structures** - deal with data in secondary storage

**Main memory** - fast storage where data is being raapidly manipulated 
	- Fast
	- Small
	- Volatile, i.e. data is lost on power failure

**Secondaty Storage** - reliable, long-term storage for massive data 
	 - Big(since it is cheap)
	 - Stable(non-volatile, i.e. data is not lost at power failres)
	 - Slow

## File systems 

File structures should
- Minimize number of trips to disk when searching for data
- Grouping related info for easier data access and search

Ierarchy
- Data is organized into files.
- Files are organized into database pages (blocks) or tables
- Database pages are organized into records
- Records are organized into fields

## Database Types

Databases can be classified accoring to:
- Number of Users
- Database Locations
- Expected type and extent of use

**Types**:
- **Centralised DB** - data located at a single site
- **Distributed DB** - data distributed across several different sites
- **Operational DB** - supports a company’s day-to-day operations
- **OLAP systems** - store historical data to be used for tactical or strategic decisions and for any type of data analtics.

By structure
Structured - formatted 
Unstructured - stored in the way they were got
Semi-structures - structured but a little bit

## DBMS
- Define (create) a particular database in terms of its data types, structures, and constraints (creating a model) 
- Construct or Load the initial database contents on a secondary storage medium 
- Manipulate the database: 
	– Retrieval: Querying to retrieve specific data, generating reports 
	– Modification: Insertions, deletions and updates to its content 
	– Accessing the database through Web applications 
- Enforce rules 
- Control concurency 
- Provide security and data privacy 
- Perform data backup and recovery 
- Optimize queries 
- Share a database allowing multiple users and programs to access the database simultaneously

Behind the scenes the DBMS has: 
- Query optimizer 
- Query engine 
- Storage management 
- Transaction Management (concurrency, recovery)


[[DDL]]
[[DML]]

