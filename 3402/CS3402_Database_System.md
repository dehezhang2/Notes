# CS3402 Database system

--------

## Lecture 01: Entity-Relationship (ER) Model

---------

* Definition of **ER model**: describes *interrelated things of interest* in a specific domain of knowledge. Becomes an abstract data model, that defines a data or information structure which can be implemented in a database. Composed of:

  * Entity types(classify the things of interest)
  * Specifies relationships: instances of those entity types

* Entity, Entity type and Entity Set

  * **Entity**: a thing capable of an independent existence that **can be uniquely identified** and exists either **physically or logically**. (represented as rectangle)(object)
  * **Entity type**: collection of entities that have the **same attributes**(class)
  * **Entity set**: set of entities of the same type(a set of objects)

* Relationship, Relationship types and  Relationship Set

  * **Relationship** (ties): captures how entities are related to one another. Relationships can be thought of as *verbs, linking two or more nouns(entities)*. For example, a work_for relationship between an employee and a department.(represented as a diamond )
  * **Relationship type**(same kinds of ties) : Defines a relationship among entities of certain entity types
    * **Degree** of a relationship type: **number of participating ==entity types==**
      * binary(ternary) relation type: involving two(three) entity types
  * **Relationship set** (a bunch of ties) : collection of relationships all belonging to one relationship type represented in the database

* Attribute

  * Both entities and relationships can have

    ![](屏幕快照 2019-01-16 下午12.33.06.png)

  * **Key attribute** : A set of attributes (one or more attributes) that ==uniquely identify an entity== 

  * Types of attribute

    * **Simple attribute** : Has a single atomic value that ==does not contain any smaller meaningful components==
    * **Composite attributes** : composed of several components(simple attributes).
    * **Multi-valued attribute** : Has multiple values. For example, color of a product (i.e., red and white) and major of a student (i.e., computer science and mathematics).(stored as a collection)
      * In general, composite and multi-valued attributes may be nested to any number of levels although this is rare.  (Muti-valued consists of multi-valued)
    * **Derived attribute** : An attribute who value is calculated from other attributes(==need not be physically stored== within the database) 

* Value sets(domains) of attributes

  * Each simple attribute is associated with a value set (or domain)
  * The value set specifies the set of values associated with an attribute
  * Value sets are similar to data types in most programming languages(**normally do not use float in database**, unsteadily, use double)

* Constrains on relationships

  * **Participation constraint**: Indicate the minimum number of relationship instances that an entity can participate in

    * **Total participation** requires that each entity is involved in the relationship.
      In other words, an entity must exist related to another entity(represented by **double lines** in ER model) => **Key word: at least one**
    * **Partial participation** means that not all entities are involved in the relationship. (represented by single lines in ER model)

  * **Cardinality constraint** : Indicates the ==maximum number== of relationship instances that an entity can participate in 

    * A **1:1 or one-to-one relationship** from entity type S to entity type T is one in which an entity from S is related to at most one entity from T and vice versa. 

    * An **N:1 or many-to-one relationship** from entity type S to entity type T is one in which an entity from T can be related to two or more entities from S. 

      ![](屏幕快照 2019-01-16 下午12.52.03.png)

    * A **1:N or one-to-many relationship** from entity type S to entity type T is one in which an entity from S can be related to two or more entities from T. 

    * An **N:M or many-to-many relationship** from entity type S to entity type T is one in which an entity from S can be related to two or more entities from T, and an entity from T can be related to two or more entities from S. 

    * *(min, max)* notation for relationship structural constraints 

      - This notation specifies that **each entity** participates in at least min and at most max relationship instances(of relationship) in a relationship. 

      - min must be at least 0 and at most max (0 <= min and min <= max) 

      - max must be at least 1 (max >= 1) 

* Recursive relationship type

  * A recursive relationship is one in which **the same entity participates more than once** in the relationship. The relationship should be ==marked by the role that an entity takes in the participation==(supervisor). 
  * It is also called a **self-referencing relationship** type. 

* Weak entity type

  * A **weak entity** that does not have a key attribute and is identification- dependent on another entity type. It must participate in an **identifying relationship** type with an owner or identifying entity type. In other words, weak entity type **must be owned by some owner entity type**. 
  * A weak entity is identified by the combination of: (1) its partial key and (2) the identifying entity type related to the identifying relationship type. 
    * **because partial key may be the same**
  * e.g.: 
    * Ada Chan is an employee. She has a dependent(受抚养者) Cindy Chan. 
    * Bob Chan is an employee. He has a dependent Cindy Chan. 
    * The two dependent entities are identical. 
    * The EMPYLOEE entity type owns the DEPENDENT entity type. 

* Notations for ER Diagrams

  ![](屏幕快照 2019-01-16 上午11.26.04.png)

* Case Study:

  ![](屏幕快照 2019-01-25 上午10.36.35.png)

  *   An ER diagram for the company database. 

  * 3 entities: EMPLOYEE, DEPARTMENT, and PROJECT 

  * 1 weak entity: DEPENDENT 

  * 4 relationships: WORKS_FOR, MANAGES, WORKS_ON, and CONTROLS 

  * 1 identifying relationship: DEPENDENTS_OF 

  * 1 recursive relationship: SUPERVISION 

  * The company is organized into DEPARTMENTs 

  * Each DEPARTMENT has a unique name, unique number, many EMPLOYEEs and an EMPLOYEE who manages the DEPARTMENT. 

  * A DEPARTMENT may have several locations. 

  * We keep track of the start date of the department manager and the number of employees for each DEPARTMENT. 

  * A DEPARTMENT controls a number of PROJECTs. 

  * Each PROJECT has a unique name, unique number and is located at a single location and is controlled by a DEPARTMENT. 

  * Each EMPLOYEE has social security number (Ssn), address, salary, sex, and birthdate. Ssn is a key attribute and address is composite attribute. 

  * Each EMPLOYEE works for one DEPARTMENT. Many EMPLOYEEs work for the same DEPARTMENT. 

  * Each EMPLOYEE may work on several PROJECTs. 

  * Many EMPLOYEEs work on the same PROJECT. 

  * An EMPLOYEE manages at most one DEPARTMENT. 

  * It is required to keep track the number of hours per week that each EMPLOYEE currently works on each PROJECT and the direct supervisor of each EMPLOYEE. 

  * A supervisor can supervise many EMPLOYEEs. 

  * An EMPLOYEE may have a number of DEPENDENTs. For each dependent, it is required to keep a record of name, sex, birthdate, and relationship to the EMPLOYEE. 

    ![image-20190125103614004](image-20190125103614004.png)

  * An ER diagram for the company database with structural constraints specified using (min, max) notation and role name. 

  * A DEPARTMENT has exactly one manager and an EMPLOYEE can manage at most one DEPARTMENT. 

  * An EMPLOYEE can work for exactly one DEPARTMENT but a DEPARTMENT has at least 4 EMPLOYEEs. 

  * An EMPLOYEE works on at least one project. A PROJECT has at least one worker. 

  * A DEPARTMENT can control no PROJECT or any number of PROJECTs, but a PROJECT has exactly one controlling department. 

  * An EMPLOYEE can have no dependent or many dependents, but a dependent belongs to exactly one EMPLOYEE. 

  * An EMPLOYEE has at most one supervisor and may be a supervisor supervising any number of supervisees.

----------

## Tutorial 01:ER Model

![image-20190125104023459](image-20190125104023459.png)

* Question 2: Construct an ER diagram for a car insurance company. Identify the key entities, relationships and their attributes in the ER diagram. 

  - A customer owns **at least one(total participation)** car. 

  - A car may be owned by more than one customer. 

  - An accident involves **at least one** car. 

  - A car may have a number of recorded accidents associated with it. 

    ![IMG_AAD29810382F-1](IMG_AAD29810382F-1.jpeg)

* Question 3:  Construct an ER diagram for a hospital. Identify the key entities, relationships and their attributes in the ER diagram. 

  - The hospital has a set of patients and a set of medical doctors. 

  - A patient may be treated by more than one doctor. 

  - A doctor may have a number of patients. 

  - A log of the various conducted tests and results is associated with each patient. 

    ![IMG_77A7AAF5726F-1](IMG_77A7AAF5726F-1.jpeg)

* Steps to draw a ER diagram

  * Entities: customer,car, accident
  * Relationships: owns involve 
    * Partial/Total Participation
    * Constraints on Relationship
  * Attributes/Key Attributes

--------------

## Lecture 02: Relational Model

-----------

* Many database implementations are always based on **relational approach** 

  * ER diagram => relation model

* Relation : Looks like a table of values

  * A relation contains a set of **rows (tuples(元组))** and each **column (attribute)** has a column header that gives an indication of the meaning of the data items in that column 
    - Associated with each attribute of a relation is a set of values (domain) 
    - Students(SSN:string, Name:string, GPA:double) 
  * The data elements in **each row** (tuple) represent certain facts that **correspond to a real-world entity or relationship(also multivalued attribute)**  

  ![](屏幕快照 2019-01-23 下午2.35.27.png)

* Primary Key vs Foreign Key

  * **Primary Key**: Uniquely indentify a record in the table. (We can have **only one** primary key in a table)
  * **Foreign Key**: Foreign key is a field in the table that is ==primary key in another table==(reference to other table, can be treated as a object field or pointer). (We can have **more than one** foreign key in a table )

* Relational Data Model: Basic Structure

  * Each row/turple in a relation is a record/turple (an entity)

  * Each attribute in a relation corresponds to a ==particular field of a record== 

    ![](屏幕快照 2019-01-23 下午2.49.28.png)

  * Definition Summary

    ![](屏幕快照 2019-01-23 下午2.50.33.png)

* Relation State

  * Each populated relation has many records or tuples in its relation state
  * Whenever the database is changed a new state arises (==change the data => change the state==)
  * Basic operations for changing the database:
    * Insert – add a new tuple in a relation 
    * Delete – remove an existing tuple from a relation 
    * Update – modify an attribute of an existing tuple 

* Characteristics of Relations

  * The tuple  **are not considered to be ordered**, even though they appear to be in a tabular(列成表的) form (may have dfferent presentation orders)
    - **same relation state can be with different order of tuples**
  * Values in a tuple
    * All values are considered atomic(indivisible)
    * Basic unit for manipulation(add or change)
  * Each value in a turple must be from the domain(set of values) of the attribute for that column
  * A special null value is used to represent values that are ==unknown or not available or inapplicable in certain tuples==

* From ER Diagram to Relations:

  * Step 1: Mapping of strong Entity types

    * Create a relation R that includes all the ==simple attributes== of E(The strong enity)

    * Choose ==one of the key attributes== E as the primary key for R 

    * R is called an entity relation

      ![](屏幕快照 2019-01-23 下午3.10.00.png)

  * Step 2: Mapping of weak Entity types

    * Create a relation R and includes all the simple attributes of the entity type as the attributes of R
    * Include the **primary key attribute of the owner** as the **foreign key attributes** of R
    * The primary key of R is the **combination** of(1) the **primary key of the owner** and(2) the **partial key of the weak entity type**(may be the name of the dependence)

  * Step 3: Mapping of 1:1 Relation**ship** types

    * Identify relations that correspond to the entity types participating R (Says S and T)
    * Approaches:
      * **Foreign key approah**(let one of the entity remember the relationship) used in the example
        * Choose one of relations(says S, normally the total participation side) and include the primary key of T as the foreign key in S
        * Include all the simple attributes of the relationship as the attributes of S
      * Merged relationship approach: merge the 2 entity types and the relationship(simple attributes) into a single relation (**not efficient**)
      * Cross reference or **relationship relation approach**
        * Set up a third relation **R** for the purpose of cross-referencing(including) the **primary keys of the two relations S and T** representing the entity types
        * Also including the primary key attributes of S and T as foreign keys to S and T respectively
        * primary key of R will be **one of the two foreign keys** (because it is 1: 1 relation, 1 key is enough to identify a relation) 

  * Step 4: Mapping of 1:N Relationship Types(let N-side remember the relation=>more efficient)

    * Identify relation S that represents participating entity type at **N-side** of relationship type
    * Include **the primary key of relation T as the foreign key in S** 
    * Include the **simple attributes** of the 1:N relationship type as the attributes of S 
    * Alternative approach(create a new relationship)
      * Use the relationship relation option as in the third approach for binary 1:1 relationships, but the **primary key of R will be two foreign keys of both involvoing entities**

  * Step 5: Mapping of Binary M:N Relationship Types

    * Create a new relation R
    * Include all primary key of the participating entity types as the foreign key attributes in R
    * The **combination of all foreign key attributes** forms the primary keys of R
    * Include **all the simple attributes** of M:N relationship type as attribute of R

  * Step 6: Mapping of Multivalued Attributes

    * Create a new relation R
    * Primary key of R. is the **combination of A and the primary key attribute of "owner"(relationship or entity) that has A as an attribute**
    * If the multivalued attribute is composite, include its simple components. 

  * Step 7: Mapping of N-ary Relationship Types

    * Create a new relation to represent R

    * Include **primary keys of participating entity types** as  foreign keys

    * Include all the **simple attributes of R** as the attributes of S 

    * The primary key of S is a combination of **all the foreign keys that reference the relations representing the participating entity types** 

      ![](屏幕快照 2019-01-23 下午3.52.36.png)

  * The example

    ![](屏幕快照 2019-01-23 下午3.10.32.png)

  * Terms

    ![](屏幕快照 2019-01-23 下午3.53.50.png)



## Tutorial 02 : Relational Model

------

![image-20190131123217182](image-20190131123217182.png)

* (a)For each strong entity type
  * Include simple (or atomic) attributes of the entity
  * include components of composite attributes
  * Identify the primary key from the key attributes
  * Do not include : non-simple component of composite attributes, derived attributes, multivalued attributes (not yet)
  * Employee(<u>SSN</u>, Fname, Lname)
  * Department(<u>Number</u>, Name)
* (b) Weak Entity(partial key, foreign key, simple attributes)
  * **Dependent**(<u>Name</u>,<u>EmployeeSSN</u>,Relationship(simple_attr))
* (c) Binary 1:1 relation ship type(==total side remember the information==)
  * Options: store the Manager information into Dept or store Dept information in manager
    * choose the total participation side to store the other side => avoid empty entry to save memory
  * **Department**(<u>Number</u>, Name, **ManagerSSN**, **StartDate**)
* (d) Binary 1:N Relationship type(N side remember the information)
  * **Employee** (<u>SSN</u>, Fname, Lname, **SupervisorSSN**)
* (e) Binary M:N Relationship type(==create new relation type==)
  * **Work_for**(**<u>EmployeeSSN,DeptNum</u>**,simple_attrs)
* (f) Multi-valued attribute(primary key of owner, simple_attrs values)(they are all prime keys) (Why??)
  * each value create an entry
  * **Dept_location**(**<u>DeptNum,single Location_value</u>**)

## Lecture 03: Structured Query Languages

---------

* Relational Query Language :

  * Data Definition Language (DDL): standard commands for defining the different structures in a database. DDL statements create, modify, and remove database objects such as tables, indexes, and users, Common DDL statements ate CREATE, ALTER, and DROP
  * Data Manipulation Language (DML): standard commands for dealing with th**e manipulation of data present in database**. Common DDL statements SELECT, INSERT, UPDATE, and DELETE. 
  * Each statement in SQL ends with a semicolon(;)

* `CREATE SCHEMA ` Statement

  * A schema is a way to **logically group objects in a single collection and provide a unique namespace for objects**. 

  * The `CREATE SCHEMA` statement is used to create a schema. A schema name **cannot exceed 128 characters**. Schema names must be **unique within the database**. 

  *  Syntax

    ```SQL
    CREATE SCHEMA schemaName AUTHORIZATION user-name 
    ```

    

  * Example

    ```SQL
    CREATE SCHEMA COMPANY AUTHORIZATION ‘Jsmith’; 
    ```

* `CREATE TABLE` Statement

  * A `CREATE TABLE` statement creates a table. Tables contain **columns and**
    **constraints(prime-key, foreign key, data type, simple attributes)**, rules to which data must conform. Table-level constraints
    specify a column or columns. Columns have a data type and can specify
    column constraints (column-level constraints).

    ![image-20190130114238286](image-20190130114238286.png)

    ![image-20190130121202991](image-20190130121202991.png)

    ![](屏幕快照 2019-01-30 下午12.16.18.png)

* Table Manipulation

  *  The` ALTER TABLE` statement allows you to: 
    - Add a column to a table 
    - Add a constraint to a table 
    - Drop a column from a table 
    - Drop an existing constraint from a table 
    - Increase the width of a VARCHAR or VARCHAR FOR BIT DATA column 
    - change the default value for a column 
  * `DROP TABLE` statement removes the specified table.  
  * The `TRUNCATE TABLE` statement allows you to quickly remove all content from the specified table and return it to its initial empty state. 

* `SELECT` Statement

  * The basic statement for retrieving(getter) information from a database

    ```SQL
    SELECT <attribute list>
    // A list of attrbibute names whose values are to be retrieved by the query
    FROM <table list> 
    // a list of relation names required to process the query
    WHERE <condition> 
    // condition is a boolean expression
    ```

  * try one of single/double quotation for a string

    ![image-20190130122300986](image-20190130122300986.png)

    ![image-20190130123100100](image-20190130123100100.png)

    ![image-20190130123417530](image-20190130123417530.png)

    * `WHERE` will find the information according to the attributes' name

* Ambiguous Attribute Names

  * Same name can be used for two (or more) attributes in different relations 

    - As long as the attributes are in different relations 

    - Must qualify the attribute name with the relation name to prevent ambiguity (Name space)

      ![image-20190130124655061](image-20190130124655061.png)

* Aliasing, Renaming and Tuple Variable

  * Aliases or tuple variables: Declare alternative relation names E and S to refer to the EMPLOYEE relation twice in a query

  * e.g. For each employee, retrieve the employee's first and last name and the first and last name of his of her immediate supervisor

    ```sql
    SELECT E.Fname, E.Lname, S.Fname, S.Lname
    FROM EMPLOYEE AS E, EMPLOYEE AS S	// E and S are alias
    WHERE E.Super_ssn=S.Ssn
    ```

  * Recommended practice to **abbreviate names and to prefix same or similar attribute** from multiple tables

  * Attributes can also be aliased

    ```sql
    EMPLOYEE AS E (Fn, Mi, Ln, Ssn, Bd, Addr, Sex, Sal, Sssn, Dno)
    ```

  * Note that the relation `EMPLOYEE` now has a variable name `E` which corresponds to a tuple variable 

  * The “AS” may be **dropped in most SQL implementations** 

    ```sql
    EMPLOYEE E (Fn, Mi, Ln, Ssn, Bd, Addr, Sex, Sal, Sssn, Dno) 
    ```

* Unspecified `WHERE` Clause(分句)

  * Missing `WHERE` clause: Indicates no condition on tuple selection(select ALL)

  * The resultant effect is a CROSS PRODUCT (`JOIN` n x m)

    * Result is all possible tuple combinations between the participating relations

      ![image-20190130164824925](image-20190130164824925.png)

  * Specify an asterisk\*: Retrive all the attributes values of the **selected tuples**

* Table as Sets in SQL

  * The `ALL` and `DISTINCT` keywords determine whether duplicates are eliminated from the result of the operation

    * `DISTINCT` : Result have no duplicate row(**default**)
    * `ALL` : May have duplicate row(depends on the original data set)

    ```sql
    SELECT DISTINCT Salary
    ```

  * `SELECT` statement using the set operators `UNION`, `INTERSECT` and `MINUS`, all set operators have equal precedences

  * Each `SELECT` statement within the operator must have the **same number of fields** in the result sets with similar data types.

  * ` UNION` operator 

    * The UNION operator is used to combine the result sets of 2 or more SELECT statements. It **removes duplicate rows** between the various SELECT statements. 

  * `UNION` ALL operator 

    * It returns all rows from IANs SELECT statements. 

    ```sql
    SELECT column_name(s) FROM table1
    UNION
    SELECT column_name(s) FROM table2;
    ```

  * `INTERSECT` operator 

    * The INTERSECT operator is used to return the results of 2 or more SELECT statements.It only returns the rows selected by all queries or data sets. In other words, if a record exists in one query and not in the other, it will be omitted from the INTERSECT results. 

  * `MINUS` operator 

    * The MINUS operator is used to return all rows in the first SELECT statement that are not returned by the second SELECT statement. Each SELECT statement will define a dataset. The MINUS operator will retrieve all records from the first dataset and then remove from the results all records from the second dataset. 

* `LIKE` Conditions

  * The `LIKE` condition allows wildcards(通配符) to be used in the `WHERE` clause of a `SELECT`, `INSERT`, `UPDATE`, or `DELETE ` statement. This allows you to perform pattern matching.

    | Wildcard | Explanation                                                  |
    | -------- | ------------------------------------------------------------ |
    | %        | Allows you to match any string of any length (including zero length) |
    | _        | Allows you to match on a single character                    |

  * select first_name begins with 'P'

    ```sql
    SELECT first_name
    FROM customers
    WHERE customers.last_name LIKE 'P%'		
    ```

* `ORDER BY` Clause

  *  The `ORDER BY` clause is used to sort the records in your result set. The `ORDER BY` clause can only be used in `SELECT` statements. 

  * Syntax: `ORDER BY expression [ ASC | DESC ] `

    - expressions: The columns or calculations that you wish to 

      retrieve

    - ASC: Optional. It sorts the result set in ascending order by expression (default, if no modifier is provider). 

    - DESC: Optional. It sorts the result set in descending order by expression. 

    - There may be many of the condition, when  first condition is same

  * e.g.: List the entire borrow table in descending order of amount, and if
    several loans have the same amount, order them in ascending order by loan#:

    ```sql
    SELECT *
    FROM Borrow
    ORDER BY amount DESC, loan# ASC;
    ```

* `INSERT` statement: insert single/ multiple records

  * insert single record using the `VALUES` keyword

    ```sql
    INSERT INTO target_table (column1, column2, ... column_n) 
    VALUES (expression1, expression2, ... expression_n);
    ```

  * insert multiple records using a `SELECT` statement

    ```sql
    INSERT INTO target_table (column1, column2, ... column_n) 
    SELECT expression1, expression2, ... expression_n 
    FROM source_table
    [WHERE conditions];
    ```

  * e.g.: ![image-20190130172803112](image-20190130172803112.png)

* `DELETE` Statement: delete a single/multiple records from a table

  ```sql
  DELETE FROM target_table
  [WHERE conditions;]
  ```

  * ​	table: The table that you wish to delete records from. 
  * `WHERE` conditions: Optional. The conditions that must be met for the records to be deleted. If no c**onditions are provided, then all records from the table will be deleted.** 
  * Example: Delete all records from the employee table where the first_name is Bob 

* `UPDATE` Statement: Used to update exsiting records in a table

  ```sql
  UPDATE table
  SET column1 = expression1,
  	column2 = expression2, ...
  	column_n = expression_n
  [WHERE conditions];
  ```

  * e.g.: Update the last_name to 'Bob' in the employee table where the employee_id is 123, and increase the balance by 5%

    ```sql
    UPDATE employee
    SET last_name = ‘Bob’, balance = balance*1.05 
    WHERE employee_id = 123;
    ```

* Nested queries and set comparisons

  * Nested queries

    * `SELECT-FROM-WHERE` blocks within `WHERE` clause of another query 
    * For example, some queries require that existing values in the database be fetched and then used in a comparison condition 

  * Comparison operator IN

    * Compares value v with a set (or multiset) of values v

    * Evaluate to `TRUE` if v is one of the elements in V

      ![image-20190130181352775](image-20190130181352775.png)

  * `=ANY` (or `=SOME`) operator returns `TRUE` if the value b is equal to **some value** in the set V and is hence equivalent to `IN`

  * `=ALL` returns `TRUE` if the value b is equal to all the values in the set V

  * Other operators that can be combined: >, >=, < , <= and <>(!=)

  * e.g.: 

    * Find the last name and first name of the employees with salary higher than all the employees in the department with Dno=5 

    ```sql
    SELECT Lname, Fname
    FROM Employee
    WHERE Salary>ALL(SELECT salary
                     From	Employee
                     WHERE	Dno = 5);
    ```

    * Find the name of braches that not the least assets

    ```sql
    SELECT DISTINCT T.cname 
    FROM Deposit T
    WHERE assets > SOME (SELECT assets
    					 FROM Branch
    					 WHERE b-city = “Central”);
    //or
    SELECT X.bname
    FROM Branch X, Branch Y
    WHERE X. assets > Y.assets AND Y.b-city= “Central”;
    
    ```

    * Find all customers who have an account at some branch in which Jones has an account

      ```sql
      SELECT DISTINCT T.cname 
      FROM Deposit T
      WHERE T.cname != “Jones”
      	  AND T.bname IN(SELECT S.bname
                           FROM Deposit S
                           WHERE S.cname = "Jones");
      //A set of branch name with “Jones” as cname.
      SELECT DISTINCT T.cname
      FROM Deposit S, Deposit T
      WHERE S.cname = “Jones” AND S.bname = T.bname
      		AND T.cname != S.cname;
      ```

* `EXISTS` Condition: 

  * `EXISTS` : The EXISTS operator is used to test for the existence of any record in a subquery. The EXISTS operator returns true if the subquery returns one or more records.

  * `NOT EXISTS` condition: return true when there is no answer

  * Thus, **the sub selection always have the information from super selection in order to return the information**

  * e.g.: 

    * Find all customers of Central branch who have an account there but no loan there

      ```sql
      SELECT C.cname 
      FROM Customer C 
      WHERE EXISTS
      			(SELECT *
      			 FROM Deposit D
      			 WHERE D.cname = C.cname
      			 AND D.bname = “Central”)
      	  AND NOT EXISTS
      			(SELECT *
      			 FROM Borrow B
      			 WHERE B.cname = C.cname
      			 AND B.bname = “Central”);
      ```

    * Find braches having greater assets than all branches in N.T

      ```sql
      SELECT X.bname
      FROM Branch X
      WHERE NOT EXISTS(SELECT *
                       FROM Brach Y
                       WHERE Y.b-city="N.T."
                       	AND Y.assets>=X.assets);
      //or
      SELECT bname
      FROM Branch
      WHERE assets>ALL(SELECT assets
                       FROM Brach
                       WHERE b-city="N.T.")
      ```

    * Find all customers who have a deposit account at ALL braches located in Kowloon(no branch do not contain its deposit)

      ```sql
      SELECT DISTINCT S.cname
      FROM Deposit S
      WHERE NOT EXIST(
          (
              SELECT bname
           	FROM Branch
           	WHERE b-city = "Kowloon"
          )
          MINUS(
          	SELECT T.bname
              FROM Deposit T
              WHERE S.cname = T.cname
          )
      );
      所有的S使得 不存在(在九龙但不包含S的branch)
      ```

* Aggregate(总数) Functions

  * Built-in aggregate functions: `COUNT`, `SUM`, `MAX`, `MIN`, `AVG`

  * summarize information from multiple tuyples into a single tuple

    ```sql
    SELECT SUM(Salary), MAX(Salary), MIN(Salary), AVG(Salary)
    FROM EMPLOYEE;
    ```

  * e.g.: Find the sum of the salaries of all employees of the 'Reasearch' department, as well as the maximum salary, the minimum salary, and the average salary in this department

    ```sql
    SELECT SUM(Salary), MAX(Salary), MIN(Salary), AVG(Salary)
    FROM EMPLOYEE, DEPARTMENT
    WHERE Dno = Dnumber AND Dname = 'Research';
    ```

  * Retrieve the total number of employees in the company

    ```sql
    SELECT COUNT(*)
    FROM EMPLOYEE;
    ```

  * Retrieve the number of employees in the 'Reasearch' department

    ```sql
    SELECT COUNT(*)
    FROM EMPLOYEE, DEPARTMENT
    WHERE Dno = Dnumber AND Dname = "Reasearch"
    ```

  * Count how many different salary values in the data base

    ```sql
    SELECT COUNT(DISTINCT Salary)
    FROM EMPLOYEE
    ```

  * Retrieve the names of all employees who have two or more dependents

    ```sql
    SELECT Lname, Fname
    FROM EMPLOYEE
    WHERE (
        SELECT COUNT(*)
        FROM DEPENDENT
        WHERE SSN=ESSN
    ) >= 2 ;
    ```

* GROUP BY Clause(used to construct a new table, each row is identified by the attribute used to group)

  * group tuples by some of its attributes

    * The same value of attributes for group members called **grouping attribute(s)**, and the aggregate function is applied to each subgroup independently

    * SQL has the GROUP BY clause for this purpose

    * The **GROUP BY clause** specifies the grouping attributes, which should also appear in the SELECT clause => **value resulting from applying each function to a group of tuples** appears along with the value of the grouping attributes

    * e.g.: For each department, retrieve the department number, the number of employees in the department, and their average salary

      ```sql
      SELECT Dno, COUNT(*), AVG(Salary)
      FROM EMPLOYEE
      GROUP BY Dno
      ```

    * For each project, retrieve the project number, the project name, and the number of employees who work on that project

      ```sql
      SELECT Pnumber, Pname, COUNT(*)
      FROM PROJECT, WORKS_ON
      WHERE Pnumber=Pno
      GROUP BY Pnumber, Pname
      ```

* HAVING Clause(conjunction with the GROUP BY clause)

  * Retrieve the values of the aggregate functions only for **groups that satisfying certain conditions**(select some rows in the GROUP BY table)

  * Example 1: For each project on which ==more than two employees work==,
    retrieve the project number, the project name, and the number of
    employees who work on the project.

    ```sql
    SELECT Pnumber, Pname, COUNT(*)
    FROM PROJECT, WORKS_ON
    WHERE Pnumber=Pno
    GROUP BY Pnumber, Pname
    HAVING COUNT(*)>2
    ```

    * `WHERE` limit the tuples to which functions applies)(correspond to WORKS_ON), `HAVING` serves to choose groups

  * Example 2: For each department that has more than five employees,
    retrieve the department number and the number of its employees who are marking more than $40,000.

    ```sql
    SELECT Dname, COUNT(*)
    FROM DEPARTMENT, EMPLOYEE
    WHERE Dnumber = Dno AND Salary>40000
    GROUP BY Dname
    HAVING COUNT(*)>5
    ```

    * This is **incorrect** because it will select only departments that have more than five employees who earn more than $40,000. This is because the WHERE clause is executed first to select individual tuples, and then the HAVING clause is applied later to select individual groups of tuples.

    ```sql
    SELECT Dname, COUNT(*)
    FROM DEPARTMENT, EMPLOYEE
    WHERE Dnumber = Dno AND Salary>40000 AND Dno in
    		(
            	SELECT Dno
                FROM EMPLOYEE
                GROUP BY Dno
                HAVING COUNT(*)>5
            )
    GROUP BY Dnumber;
    ```

* Views(Virtual Tables)

  * A VIEW is a virtual table that does not physically exist. 

  * A view contains rows and columns, just like a real table. The fields in a 

    view are fields from one or more real tables in the database. 

  * You can add SQL functions, WHERE, and JOIN statements to a view and present the data as if the data were coming from one single table. 

  * A view always shows up-to-date data! The database engine recreates the data, using the view's SQL statement, every time a user queries a view. 

  * When you update record(s) in a VIEW, it updates the records in the underlying tables that make up the View. However, most SQL-based DBMSs restrict that a modification is permitted through a view ONLY IF the view is defined in terms of ONE underlying table. 

    ![image-20190210175356966](image-20190210175356966.png)

* NULL Values

  * Information can be very often incomplete in the real world

  * Unknown attributes are assigned a null value

  * One proposal to deal with NULL values is by using 3-valued logic

    ![image-20190210175502133](image-20190210175502133.png)

  * Syntax: expression IS NULL

    * Expression: The value to test whether it is a null value 
    * If *expression* is a NULL value, the condition evaluates to TRUE. 
    * If *expression* is not a NULL value, the condition evaluates to FALSE. 

* Summary:

  ![image-20190210175704945](image-20190210175704945.png)

  ![image-20190210175728566](image-20190210175728566.png)

----------------



