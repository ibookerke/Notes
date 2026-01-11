Alters the physical order of data in the table to match the index order.

Might be useful for range based search in a table.

Example:
```SQL
CREATE CLUSTERED INDEX idx_clustered_salary ON employees(salary);
```

When you are creating the clustered index on a table -> it rearranges the physical order of data, so it will be easier to search for DBMS. 


Hence, there could be only one clustered index in a table. 
Regularly, the clustered index is created for primary key