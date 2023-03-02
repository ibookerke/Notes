ER Model is a popular high-level conceptual data model.


## DB design steps
- Requirements collection and analysis
- Create a conceptual schema.
	- concise description of the data requirements 
- The actual implementation using a DBMS
	- data model mapping (logical design): map the conceptual schema into the data model of the chosen DBMS.
- Physical design
	- internal storage structures, file organizations, indexes, etc. are specified.


## Diagram Notation
- **Entity** – basic thing or object that exists independently (e.g. - person, car, employee).
- Every entity is further described by its properties called Attributes
**Key attributes** – attributes that uniquely define an entity. (we underline a key)
**Weak entity Types** - entity types that doesn't have key attribute

![[Pasted image 20221109104952.png]]

## Relationships, Roles, Constains
Whenever an attribute of one entity type refers to another entity type, some relationship exists.
**Relationship degree** - number of participating entities.

Each entity type that participates in a relationship type plays a particular role in the relationship.
**Self-referencing/Recursive** relationship - when the same entity type participates more than once in a relationship type in different roles.

Participation Constraints and Existence Dependencies: specifies whether the existence of an entity depends on its being related to another entity via the relationship type. 

Two types: **total** (two lines) and **partial** (one line) participation
