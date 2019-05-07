# Short cheat sheet for CS3402

--------

## SQL

-----

- `CREATE SCHEMA` Statement

  - A schema is a way to **logically group objects in a single collection and provide a unique namespace for objects**. => like a package (different with the schema in relational model)

  - The `CREATE SCHEMA` statement is used to create a schema. A schema name **cannot exceed 128 characters**. Schema names must be **unique within the database**. 

  - Syntax

    ```SQL
    CREATE SCHEMA schemaName AUTHORIZATION user-name；
    ```

    

  - Example

    ```SQL
    CREATE SCHEMA COMPANY AUTHORIZATION ‘Jsmith’; 
    ```

- Clustered practice questions

  - Relations of department
    - EMPLOYEE(FNAME, MINIT, LNAME, <u>SSN</u>, BDATE, ADDRESS, SEX, SALARY, SUPER_SSN, DNO)
    - DEPARTMENT(DNAME, <u>DNUMBER</u>, MGR_SSN, MGR_START_DATE)
    - DEPT_LOCATIONS(<u>DNUMBER</u>, <u>DLOCATION</u>)
    - WORKS_ON(<u>ESSN</u>, <u>PNO</u>, HOURS)
    - PROJECTS(PNAME, <u>PNUMBER</u>, PLOCATION, DNUM)
    - DEPEDENT(<u>ESSN</u>, <u>DEPENDENT_NAME</u>, SEX, BDATE, RELATIONSHIP)
  - Relations for mid-term
    - PERSON(<u>PID</u>, PNAME)
    - EVENT(<u>EID</u>, ENAME, START_TIME, END_TIME)
    - INVITED(<u>PID, EID</u>, ATTENDED)

  - Type I: Simple retrieve

    - Retrieve the **birth date** and **address** of the employee(s) whose name is ‘John B. Smith’.

      ```sql
      SELECT Bdate, Address
      FROM EMPLOYEE
      WHERE Fname = 'John'
      AND 	Minit = 'B'
      AND		Lname = 'Smith';
      ```

  - Type II: Retrieve with join condition

    - Retrieve the **name** and **address** of all employees of all employees who **work for** the **‘Research’** department

      ```sql
      SELECT FNAME, Address
      FROM EMPLOYEE, DEPARTMENT
      WHERE Ssn = Essn
      AND		Dname = 'Research';
      ```

    - For every project located in ’**Stafford**’, list the **project number**, the controlling **department number**, and the **department manager’s last name** 

      ```sql
      SELECT PNUMBER, DNUMBER, LNAME
      FROM PROJECT P, DEPARTMENT D, EMPLOYEE E
      WHERE D.DNUM = P.DNUMBER
      AND		D.MGR_SSN = E.SSN
      AND		P.PLOCATION = 'Stanford'
      ```

  - Type III: Use alias name to retrieve the information of recursive relationship or do the comparation within one relation

    - For each employee, retrieve the employee’s **first and last name** and the **first and last name of his or her immediate supervisor.** 

      ```sql
      SELECT E1.FNAME, E1.LNAME, E2.FNAME, E2.LNAME
      FROM EMPLOYEE E1, EMPLOYEE E2
      WHERE E1.SUPER_SSN = E2.SSN
      ```

    - Mid-term question: Retrieve the ids and names of all persons who have attended to two distinct events that have the same start time and end time

      ```sql
      SELECT 
      ```

      

  - Select all EMPLOYEE **Ssns** 

    ```sql
    
    ```

  - Select all **combinations of EMPLOYEE Ssn and DEPARTMENT Name** in the database

    ```sql
    
    ```

  - Make a list of all **project numbers** for projects that involve an employee whose last name is ’Smith’, either as a **worker or as a manager of the department** that controls the project

    ```sql
    
    ```

  - Find all of the customers whose first_name begins with ‘P’s

    ```sql
    
    ```

  - Delete all records from the employee table where the first_name is Bob

    ```sql
    
    ```

  - Update the last_name to ‘Bob’ in the employee table where the employee_id is 123

    ```sql
    
    ```

  - Increase the payment by 5% to all accounts; it is applied to each tuple exactly once.

    ```sql
    
    ```

  - Increase the payment by 6% to all accounts with balance over \$10000; all others receive 5% increase

    ```sql
    
    ```

  - Make a list of all **project numbers** for projects that involve an employee whose last name is ’Smith’, either as a **worker or as a manager of the department** that controls the project **by using nested queries**

    ```sql
    
    ```

  - Select the Essn of all employees who work the same **project and hours** as the employee Essn = “123456789”

    ```sql
    
    ```

  - Find the lasdt name and First name of the employees with salary higher than all the employees in the deparment 5

    ```sql
    
    ```

  - Find the sum of the salaries of all employees of the ‘Research’ department, as well as the maximum salary, the minimum salary, and the average salary in this department

    ```sql
    
    ```

  - Select the number of employees in ‘Research’ department

    ```sql
    
    ```

  - Select the number of different salary values in the database.

    ```sql
    
    ```

  - Retrieve the names of all employees who have **2 or more dependents**

    ```sql
    
    ```

  - For **each department**, retrieve the department number, the  number of employees in the department, and their average salary.

    ```sql
    
    ```

  - For **each project**, retrieve the project number, the project  name, and the number of employees who work on that project. 

    ```sql
    
    ```

  - For **each project** on which **more than two employees** work,  retrieve the project number, the project name, and the number of employees who work on the project

    ```sql
    
    ```

  - For each department that has more than five employees,  retrieve the department number and the number of its employees who are marking more than $40,000.

  - List in alphabetical order all customers having a loan at Kowloon branch

    ```sql
    SELECT DISTINCT CNAME
    FROM BORROW
    WHERE BNAME = 'Kowloon'
    ORDER BY CNAME;
    ```

  - List the entire borrow table in descending order of amount, and if several loans have the same amount, order them in ascending order by loan#:

    ```sql
    SELECT * 
    FROM BORROW
    ORDER BY AMOUNT DESC, 
    				 loan# ASC;
    ```

  - Find names of all branches that have greater assets than some branch located in Central

    ```sql
    SELECT BNAME
    FROM BRANCH
    WHERE ASSETS > SOME(
    	SELECT ASSETS 
      FROM BRANCH
      WHERE B_CITY = "CENTRAL"
    );
    
    SELECT DISTINCT X.BNAME
    FROM BRANCH X, BRANCH Y
    WHERE X.ASSETS > Y.ASSETS AND Y.B_CITY = "CENTRAL";
    ```

  - Find all customers who have an account at some branch in which Jones has an account

    ```sql
    SELECT DISTINCT T.CNAME
    FROM DEPOSITE T
    WHERE T.CNAME != 'JONES'
    AND T.BNAME IN(
    	SELECT S.BNAME
      FROM DEPOSITE S
      WHERE S.CNAME = "JONES";
    );
    
    SELECT DISTINCT T.CNAME
    FROM DEPOSITE T, DEPOSITE S;
    WHERE T.CNAME != 'JONES'
    AND T.BNAME = S.BNAME
    AND S.CNAME = 'JONES';
    ```

  - Find all customers of Central branch who have an account there but no loan there

    ```sql
    SELECT C.cname 
    FROM Customer C 
    WHERE EXISTS
    			(SELECT *
    			 FROM Deposit D
    			 WHERE D.cname = C.cname	(account <=> customer)
    			 AND D.bname = “Central”)
    	  AND NOT EXISTS
    			(SELECT *
    			 FROM Borrow B
    			 WHERE B.cname = C.cname	(loan <=> customer)
    			 AND B.bname = “Central”);
    ```

  - Find branches having greater assets than all branches in N.T

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
                     FROM Branch
                     WHERE b-city="N.T.")
    ```

  - Find all customers who have a deposit account at ALL branches located in Kowloon(no branch do not contain its deposit) => **better to draw a Venne diagram** 

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
    在九龙-包括他 个数为零
    //not sure correct
    SELECT DISTINCT S.cname
    FROM Deposit S
    WHERE (
    	SELECT COUNT(*)
        FROM BRANCH B, DEPOSIT T
        WHERE B.cname = T.cname
        AND B.b-city = "Kowloon"
        AND S.cname != T.cname
    )=0;
    ```

------------

## Relational Algebra

---------

* The sample data base schema

  ![image-20190303204441073](image-20190303204441073.png)

* Select the employee tuples whose department number is 4

  

* Select the employee tuples whose salary is greater than \$30.000

  

* Retrieve the ssn of all employees who either **work in** department 5 or **directly supervise** an employee who works in department 5

  

* Select all name of female employees and their dependents

  

----------

## Indexing and B+ tree

* Suppose the data record size $R$ is 100 bytes , block size $B$ is 1024 bytes, the number of records $r$ is 30,000, pointer size $P_R$ is 6 bytes, field size $V$ is 9 bytes, calculate the block access number respectively
  $$
  b_1 = {{R*r} \over B} = 30000*100/1024 = 3000\ bytes\\
  b_2 = {{b_1*(P_R+V)} \over B} = 3000*15/1024 = 45\ bytes\\
  a_1 = log_2b_1 \\
  a_2 = log_2b_2 + 1 \\
  $$

* 