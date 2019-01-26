# CS3402 Database system

--------

## Lecture 01: Entity-Relationship (ER) Model

---------

* Definition of **ER model**: describes interrelated things of interest in a specific domain of knowledge. Becomes an abstract data model, that defines a data or information structure which can be implemented in a database. Composed of:

  * Entity types(classify the things of interest)
  * Specifies relationships: instances of those entity types

* Entity, Entity type and Entity Set

  * **Entity**: a thing capable of an independent existence that **can be uniquely identified** and exists either **physically or logically**. (represented as rectangle)
  * **Entity type**: collection of entities that have the **same attributes**
  * **Entity set**: set of entities of the same type

* Relationship, Relationship types and  Relationship Set

  * **Relationship** (ties): captures how entities are related to one another. Relationships can be thought of as verbs, linking two or more nouns. For example, a work_for relationship between an employee and a department.(represented as a diamond )
  * **Relationship type**(same kinds of ties) : Defines a relationship among entities of certain entity types
    * Degree of a relationship type: **number of participating entity types**
      * binary(ternary) relation type: involving two(three) entity types
  * **Relationship set** (a bunch of ties) : collection of relationships all belonging to one relationship type represented in the database

* Attribute

  * Both entities and relationships can have

    ![](屏幕快照 2019-01-16 下午12.33.06.png)

  * **Key attribute** : A set of attributes (one or more attributes) that uniquely identify an entity 

  * Types of attribute

    * **Simple attribute** : Has a single atomic value that does not contain any smaller meaningful components
    * **Composite attributes** : composed of several components.
    * **Multi-valued attribute** : Has multiple values. For example, color of a product (i.e., red and white) and major of a student (i.e., computer science and mathematics).(stored as a collection)
      * In general, composite and multi-valued attributes may be nested to any number of levels although this is rare.  
    * **Derived attribute** : An attribute who value is calculated from other attributes(need not be physically stored within the database) 

* Value sets(domains) of attributes

  * Each simple attribute is associated with a value set (or domain)
  * The value set specifies the set of values associated with an attribute
  * Value sets are similar to data types in most programming languages(**normally do not use float in database**, unsteadily, use double)

* Constrains on relationships

  * **Participation constraint**: Indicate the minimum number of relationship instances that an entity can participate in

    * **Total participation** requires that each entity is involved in the relationship.
      In other words, an entity must exist related to another entity(represented by **double lines** in ER model)
    *  **Partial participation** means that not all entities are involved in the
      relationship. (represented by single lines in ER model)

  * **Cardinality constraint** : Indicates the maximum num per of relationship instances that an entity can participate in 

    * A **1:1 or one-to-one relationship** from entity type S to entity type T is one in which an entity from S is related to at most one entity from T and vice versa. 

    * An **N:1 or many-to-one relationship** from entity type S to entity type T is one in which an entity from T can be related to two or more entities from S. 

      ![](屏幕快照 2019-01-16 下午12.52.03.png)

    * A **1:N or one-to-many relationship** from entity type S to entity type T is one in which an entity from S can be related to two or more entities from T. 

    * An **N:M or many-to-many relationship** from entity type S to entity type T is one in which an entity from S can be related to two or more entities from T, and an entity from T can be related to two or more entities from S. 

    * (min, max) notation for relationship structural constraints 

      - This notation specifies that **each entity** participates in at least min and at most 

        max relationship instances(of relationship) in a relationship. 

      - min must be at least 0 and at most max (0 <= min and min <= max) 

      - max must be at least 1 (max >= 1) 

* Recursive relationship type

  * A recursive relationship is one in which **the same entity participates more than once** in the relationship. The relationship should be marked by the role that an entity takes in the participation. 
  * It is also called a **self-referencing relationship** type. 

* Weak entity type

  * A **weak entity** that does not have a key attribute and is identification- dependent on another entity type. It must participate in an **identifying relationship** type with an owner or identifying entity type. In other words, weak entity type **must be owned by some owner entity type**. 
  * A weak entity is identified by the combination of: (1) its partial key and (2) the identifying entity type related to the identifying relationship type. 
    * **because partial key may be the same**
  * e.g.: 
    * Ada Chan is an employee. She has a dependent Cindy Chan. 
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

  - A customer owns at least one car. 

  - A car may be owned by more than one customer. 

  - An accident involves at least one car. 

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
  * Attributes/Key Attributes
  * Partial/Total Participation
  * Constraints on Relationship

--------------

## Lecture 02: Relational Model

-----------

* Many database implementations are always based on **relational approach** 

  * ER diagram => relation model

* Relation : Looks like a table of values

  * A relation contains a set of **rows (tuples)** and each **column (attribute)** has a column header that gives an indication of the meaning of the data items in that column 
    - Associated with each attribute of a relation is a set of values (domain) 
    - Students(SSN:string, Name:string, GPA:double) 
  * The data elements in **each row** (tuple) represent certain facts that **correspond to a real-world entity or relationship(also multivalued attribute)**  

  ![](屏幕快照 2019-01-23 下午2.35.27.png)

* Primary Key vs Foreign Key

  * **Primary Key**: Unquely indentify a record in the table. (We can have **only one** primary key in a table)
  * **Foreign Key**: Foreign key is a field in the table that is primary key in another table(reference to other table, can be treated as a object field or pointer). (We can have **more than one** foreign key in a table )

* Relational Data Model: Basic Structure

  * Each row/turple in a relation is a record/turple (an entity)

  * Each attribute in a relation corresponds to a particular field of a record 

    ![](屏幕快照 2019-01-23 下午2.49.28.png)

  * Definition Summary

    ![](屏幕快照 2019-01-23 下午2.50.33.png)

* Relation State

  * Each populated relation has many records or tuples in its relation state
  * Whenever the database is changed a new state arises
  * Basic operations for changing the database:
    * Insert – add a new tuple in a relation 
    * Delete – remove an existing tuple from a relation 
    * Update – modify an attribute of an existing tuple 

* Characteristics of Relations

  * The tuple  **are not considered to be ordered**, even though they appear to be in a tabular form (may have dfferent presentation orders)
    - **same relation state can be with different order of turples**
  * Values in a tuple
    * All values are considered atomic(indivisible)
    * Basic unit for manipulation(add or change)
  * Each value in a turple must be from the domain(set of values) of the attribute for that column
  * A special null value is used to represent values that are unknown or not available or inapplicable in certain tuples

* From ER Diagram to Relations:

  * Step 1: Mapping of strong Entity types

    * Create a relation R that includes all the simple attributes of E(The strong enity)

    * Choose one of the key attributes E as the primary key for R 

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
        * Choose one of relations(says S) and include the primary key of T as the foreign key in S
        * Include all the simple attributes of the relationship as the attributes of S
      * Merged relationship approach: merge the 2 entity types and the relationship(simple attributes) into a single relation (**not efficient**)
      * Cross reference or **relationship relation approach**
        * Set up a third relation **R** for the purpose of cross-referencing(including) the **primary keys of the two relations S and T** representing the entity types
        * Also including the primary key attributes of S and T as foreign keys to S and Tm respectively
        * primary key of R will be **one of the two foreign keys** (because it is 1: 1 relation, 1 key is enough to identify a relation) 

  * Step 4: Mapping of 1:N Relationship Types(let N-side remember the relation)

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





