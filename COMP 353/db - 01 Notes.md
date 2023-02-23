-   There are 3 types of inputs to DBMS:
	-   Queries
	-   Transactions, i.e., data Modifications
	- Schema Creations/ Modifications
- Let R(A**1**,…,A**n**) be a relation schema and _r be any_ instance of R. Suppose _r_ has _m_ tuples. Which of the following is the number of ways in which _r_ may be represented in the relational model?
	- m! * n!
- Types of Data Models
	- E/R diagram 
	- Relational model 
	- Object oriented data model 
	- Logical data model (ODL)
- Three View of Data
- **Internal  (physical) level**
		- A block of consecutive bytes actually holding the data
-   **Conceptual (logical) level**
	- type emp = record
	- SIN : integer;
	- name : string;
-   **External (logical) level**
	- View 1 : (emp.name, emp.address)
	- View 2 : (emp.SIN, emp.salary)
- A database _instance_ is the current content of the DB
-   A database _schema_ is the structure of the data (relations/classes), described in some suitable data model
### Data Independence
> the ability to modify definition of schema at one level with little or no affect on the schema (s) at a higher level

#### Logical Independence
> Ability to modify logical schema with little or no affect/change to rewrite the application programs
#### Physical independence 
> -   Ability to modify physical schema with little or no  impact on the conceptual schema or the application programs, i.e., _the possibility of having separate schemas at the physical and conceptual levels_
## DB architecture 
![[Screenshot 2023-02-21 at 6.49.05 PM.png]

-   The SQL query language components:
	-   DDL
	-   DML
### Understanding NULL values 
- Nulls are counted when grouping but ignored when aggregating.
- NULL = NULL returns NULL 
- 