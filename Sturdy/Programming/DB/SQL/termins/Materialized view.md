Mostly like [[SQL View]] but the result of select query is stored in the database as separate physical table. 


It is commonly used when the freshness of data is not that important and the select query is performed very often. Hence, the data requested form the materialized view will be fetched immediately without processing the query. The schedule for updating materialized view could be configured or even implemented manually.




