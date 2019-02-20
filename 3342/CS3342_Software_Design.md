# CS3342 Software Design

--------

## Lecture 01 Introduction to Software Engineering and Design

-------

### What is Software

* Software is a set of items or objects that form a “**configuration**” that includes 
  * **programs** (i.e., source code, executable code) which are instructions
  * **documents** (requirements, design document, test plan, user guide, etc.) ‘describe the program’
  * **data structure** that ‘enable program’ to work. 
* Software is the **Product** that SW engineers design and build
  * produces, manages, acquires, modifies, displays, or transmits information
* Software is **logical rather than physical**
* Software is a **vehicle for delivering a product/service**
  * **Supports or directly** provides system **functionality** (e.g., banking system, inventory control, CRM)
  * **Controls** other programs (e.g., an operating system)
  * Enable communications (e.g., networking software)
  * Helps build other software (e.g., software tools)
* Quality of software
  * It works(must do the task correctly and completely), thus the first step in the development process is to understand the SW REQUREMENT
    * Format of input and output
    * Processing details
    * Performance
    * Error and handling procedures
    * Standards
  * Can be read and easily understood: document the code
  * Can be modified: accommode for new requirements and changes
  * Completed in time and within budget
* Software vs. Hardware
  * software is engineered not manufactured
  * software doesn't wear out
  * software is complex
  * Software is custom build (most of them) except software like *Excel, PowerPoint,* etc.
* Software Costs
  * Software costs often dominate system costs (cost of software on a PC are often greater than the hardware cost)
  * Software costs more to **maintain** than it does to **develop**. For systems with a long life, maintenance costs could be several times of development costs
* **The IEEE Definition of Software Engineering**
  * “The application of a systematic, disciplined, quantifiable approach to the development, operation, and maintenance of software; that is, the application of engineering to software.”
  * Software
    Engineering is the process of solving **users problems** by the systematic development and evolution of large, high-quality software systems within cost, time and other constraints
* Task in SE
  * Feasibility Study
  * Requirements Analysis
  * Design
  * Programming**
  * Unit test
  * Integration and system test
  * User training
  * Changeover
  * Maintenance
  * And many more…
* **Software professionals** are characterized 
  * by a relevant education and continued learning;
  * they have a holistic or system life-cycle focus; 
  * they work to industry standards; 
  * and they have a balanced approach to technical risk. 
* **Why do software project fail**
  * Poor communication(internal and external)
  * Resistance to change
  * Not reviewing project progress on a regular basis
  * Unclear Requirements
  * Unrealistic expectations
  * The absence of a good project manager
  * Moving the goalposts too often
  * not enough resource

-------------------

## Lec 02 Software Process

------------

### Part one :

* Object : thing from real world which can be quantified to mean one specific item

  * an **instance** of class
  * entity that has a state and a set of operations on that state (**a set of object attribute**)
  * Operation: provide services to other obj which request these services

* Class : represent all objects of the same kind

  * A set of related objects
  * Declarations of the attributes and services associated with an object of that class
  * represents some useful concept that existing in the **problem/solution domains**
  * may inherit attributes and operations from other classes

* OO

  * OO Programming has become the **standard programming** methodology for software engineers.
  * OO Programming is a **software programming paradigm** using “objects”, with instances of a class. 
  * In OO programming, you would design the program with the **data parts in mind, contextual information rather than procedures.**  
  * E.g Designing a smart phone…  : What kind of information/data to be stored/used? 

* Advantage of OO

  * **Easier to maintain** : Objs may be understood as stand-alone entities
  * **reuse** 
    * Objects are potentially **reusable** components.
    * For some systems, there may be an obvious mapping from real world entities to system objects.

* Rules to Name Classes

  

  ![image-20190124132542617](image-20190124132542617.png)

  * notice to model *real world* objects correctly, every attribute of the class instance must be assigned with a concrete value at any time. 

* UML![image-20190124133303293](/Users/zdh/Documents/GitHub/Notes/3342/image-20190124133303293.png)

  * Operations : 

    * **change the value** of some attribute of an obj(set)
    * **Queries** (get)

  * Reference

    * Objects communicate by *message passing*: request from one object to another asking the second object to execute one of its methods.

    ![image-20190124133942815](/Users/zdh/Documents/GitHub/Notes/3342/image-20190124133942815.png)

* State of Object

  * Objects can be in different **states**. 
  * State will change under the influence of outside circumstances
  * Use a interface and create difference states class to implement the interface

* Object Inheritance : Tool to reuse the code

  * subclass "is a (kind of)" superclass
  * generalization and inheritance
    * ***Generalisation*** is implemented as ***inheritance*** in OO programming languages
    * *Classes* may be arranged in a *class
      hierarchy* where one class (a *super-class*) is a *generalisation* of one or more other classes (*sub-classes*)
  * Sub-class inherits (all **attributes/operations/relationships**), and add attributes and operations, relationships, **redifine(override**) inherited operations
  * **Point from subclass to superclass**
  *  Do not use too often which causes difficulties of management

  ![image-20190124134601450](/Users/zdh/Documents/GitHub/Notes/3342/image-20190124134601450.png)

* Advantage of Inheritance

  * It is *an abstraction mechanism* to classify entities
  * It *supports* ***reuse***（often exist in the exam） both at the design and programming level
  * It provides a mechanism to extend or refine a class: by adding or overriding methods (or *operations*) and by adding attributes
  * The inheritance diagram is a *source of organisational knowledge about domains and systems*

* Information Hiding in OO

  * *Information hiding* enhances **maintainability** 
    because implementation details are **invisible** outside an object
  * OO languages allow an attribute to be described as **private** (invisible outside the object) 
    *  (-) minus-sign : private, (+) plus-sign : public

* Benefits of information hiding

  * change cannot affect other part of the system
  * a system consists of essentially **independent** classes
  * they **communicate by sending messages**
  * **objects do talking to each other**

### Part two:

### Software process

* Software process: A series of predictable steps, road maps, that help us to create a timely, and high-quality result (defines tasks of activities that take place during the process)
  * defines who is responsible for:
    * What?
    * when and how?
    * to reach a goal
  * Process defines ==tasks and activities== within a schedule
  * start with understanding the business requirements

### SW Process Model (Life cycle)

* Software process model

  * An abstract representation of a process
  * It describe **a process**
  * guides the software developement team
  * with a set of key activities

* Phases and components : (e.g. design phase, test phase) and each phase has 3 components:

  * set of **activities**： define, design, implement, test and maintain
  * set of **deliverables**(可交付产品): what to produce
  * Quality control **measures**: what to use to evaluate/assess deliverables 

* Process Model

  * **Waterfall Model**: Follows a ==systematic, sequential approach== to SW development that begins at the system level and progresses through analysis, design, code and testing.

    * The "god parent" of models, linear sequence of phases
    * pure model : **no phases overlap**
    * Pros: Easy; Structured; Provide a template into which methods for **analysis, design, code, testing and maintenance** can be placed.
    * Cons:
      *  Sequential, does not reflect reality
      * Does not produce a prototype
      * *Little feedback from users* until it might be too late. Therefore cannot adapt to users’ needs, lack of intelligence and adaptability
      * *Problems in the specification may be found very late (at* Coding or integration)
      * It can *take a long time* before the first version is out
      * Risky: Integration and testing occur at the end => to late
    * When to use: 
      * simple proj
      * limited amout of time
      * requirements are well understood
      * Use well-understood technologies

  * Incremental Process Models

    * Goal : provide quick basic functionality to the users

    * Process is not linear

    * **Requirements are well defined**

    * Software is completed **in small increments**

    * The system "Grows" in a number of small steps

    * 2 types:

      * Incremental Model

        ![](屏幕快照 2019-01-23 下午8.26.15.png)

        * First  build provides the **CORE** functionalities
        * Each increment “deliverable” **adds a new** functionality.
        * This is repeated until the product is complete 
        * It combines characteristics of the waterfall model and the iterative nature of the prototyping model
        * When to use: software **can be broken into increments** and each increment represent a solution

      * RAD (The Rapid Application Developement) Model

        ![](屏幕快照 2019-01-23 下午8.29.33.png)

        * Builds on the Incremental model with emphases on **short development cycle**.
        * A **speed waterfall** model
        * Components are built using this model as a fully functional units in a relatively short time
        * It **assumes that the system can be modularized(模块化)**
        * Involves multiple teams!
        * ==RAD will fail if we don’t have strong and skillful teams==

* Evolutionary(演变) Process Models

  * **Specification,development and validation** activities are carried out *concurrently*(同时) with *rapid feedback* *across these activities*

  * **Core requirements are well understood but** **additional requirements are evolving and changing fast**

    * Design most prominent(重要的) parts first
    * Usually via a visual prototype
    * Good for situations with:
      * Rapidly **changing requirements**
      * Non-committal customer(非承诺客户)
      * Vague(模糊) problem domain
    * **Advantages**
      * Do not require **full** knowledge of the requirements
      * **Iterative** (software gets more complex with each iteration)
      * Divide project into **builds** (standalone software package - binaries)
      * Allows ***feedback***, show user something sooner
      * Use to develop more complex systems 
      * Provide steady, visible progress to customer
    * **Disadvantages**
      * Time estimation is difficult
      * Project completion date may be unknown

  * **Prototyping Model**

    * Start with what is known about requirements.
    * Complete a quick design.
    * ==Build the prototype by focusing on what will be seen by the user.==(write interface first??)
    * Use the prototype to show the user and help refining(提炼) requirements.
    * Better communication
    * Advantage
      * Prototype can serve as a way for identifying requirements.
      * It is developed very quickly.
    * Disadvantage
      * Customer might think that the prototype is the final product and forget the lack of quality i.e. PERFORMANCE, RELIABILITY.
    * **When to use?**: 
      * When the customer define general ==objectives for the SW but does NOT identify details about INPUT, OUTPUT, or processing requirements.==
      * The developer is unsure of the efficiency of an algorithm, human machine interaction, etc(no implementation detail)

  * Spiral(螺旋) Model
    * Iterative (like Prototype) and controlled (like waterfall)
    * Software is developed using evolutionary releases(演变发行)
    * Complexity increase with each release
    * A spiral process rather than as a sequence of activities with backtracking
    * *Each loop* in the spiral represents *a phase in the process*. 
    * *No fixed phases* such as req. specification or design - loops in the spiral are chosen depending on what is required—*more flexible*
    * Emphasize risk analysis and management (Risks are explicitly assessed and resolved throughout the process)

  * The Spiral Model

    ![image-20190211105539941](image-20190211105539941.png)

    * Each addresses a set of "risks": Start small, explore risks, prototype, plan, repeat
    * Number of spirals is variable
    * Advantage: 
      * Can be combined with other models(as long as it can be divided into spirals)
      * risk orientation provides early warning of problems
    * Disadvantages
      * More complex
      * requires more management
    * When to use
      * very large projects, mission critical systems
      * When technical skills must be evaluated at each step

  * Concurrent Engineering Model(paralllel development)

    ![image-20190211110212834](image-20190211110212834.png)

    * It explicitly use the **divide and conquer** principle.
    * Each team works on its own component, ==typically following a spiral or evolutionary approach.==
    * There has to be some initial planning, and periodic integration.   

* Other Process Model: Component based software engineering(CBSE)

  * ==When **reuse** is a development objective==

  * Based on systematic reuse where systems are ==integrated from existing components or COTS (Commercial-off-the-shelf) systems.== (E.g., data conversion, encryption, device drivers, data mining modules)

  * The main difference is that CBSE emphases(依靠) on **composing** solutions
    from prepackaged software components or classes 

  * Key questions: Are commercial off-the-shelf components and internally-developed reusable components are available to implement the requirement; Are the interfaces for available components compatible within the architecture of the system to be built?

  * First rule of CBSE: never build what you can buy!

    Because: it becomes solution oriented, built based on features available in the components, not from customer requirements (problem-oriented). 

  * Design principles:

    * Components are independent so do not interfere with each other
    * Component implemnations are hidden
    * Communication is through well-defined interfaces;(method calls)
    * Component platforms are shared and reduce development efforts/costs

  * Component: Provide a service without regard to where the component is executing or its programming language

    * The *component interface* is published and all interactions are through the published interface;
    * An independent, executable entity
    * The services offered by a component are made available through an interface API

  * Component characteristics

    ![](屏幕快照 2019-02-11 上午11.43.18.png)

  * Considerations

    ![image-20190211114512434](image-20190211114512434.png)

    * step(1): Build up a component library
    * step(2): Develop a new system based on components

---------------

## Lecture 03 OOFundamental-Part II & Roles of Variables & UML Class Diagram

-------

### OOFundamental II

* Abstraction

  ![屏幕快照 2019-02-11 下午12.00.16](屏幕快照 2019-02-11 下午12.00.16.png)

  ![屏幕快照 2019-02-11 下午12.01.52](屏幕快照 2019-02-11 下午12.01.52.png)

  * Abstract class\<\<abstract\>\>, ... extends...
    * A special kind of class that ==cannot be instantiated== (create object).
    * Can have ==“default” implementations==, subclasses can modify. 
    * Enforce ==certain characteristics and hierarchies for all the subclasses==.
    * Support ==Multiple Inheritance: NO.== Can only inherit from one abstract class
  * Interface\<\<interface\>\>, ... implements...
    * An interface is NOT a class. It is an entity, and ==has no implementation==.
    * Only the definition of the methods without the body.
    * Cannot have “default” implementation, ==subclasses MUST implement them==.
    * Support Multiple Inheritance : Yes, can implement different Interfaces

* Polymorphism(and dynamic binding)

  ![image-20190211120835396](image-20190211120835396.png)

  * Polymorphism is an OO feature that allows a [subclass](http://en.wikipedia.org/wiki/Subclass_(computer_science)) to provide a specific implementation of a [method](http://en.wikipedia.org/wiki/Method_(computer_science)) that is already provided by one of its [superclasses](http://en.wikipedia.org/wiki/Superclass_(computer_science)).
  * Method overriding is an important feature that facilitates [polymorphism](http://en.wikipedia.org/wiki/Polymorphism_(computer_science)) in the design of [object-oriented](http://en.wikipedia.org/wiki/Object-oriented) [programs](http://en.wikipedia.org/wiki/Computer_program).

### Roles of Variables

* If a variable has **multiple purposes** to be used at the same time, the logic becomes less obvious: It is easier to introduce bugs in our program if we are unable to consistently maintain the value of the variable for all purpose

* The "Role" of a variable: is a way for developer to represent *meta-level programming knowledge*. Ten of them are very common in programs

  * **Constant/Fixed value**: A variable which is initialized without any calculation whose value does not change thereafter

    * Purpose: write once and read only
    * Example: read the radius of a circle, then print the area of the circle
      * variable ***r*** is a *fixed value, gets its value once,* never changes after that 
      * (e.g.,  the variable PI in the following example).
    * "final" in Java or "const" in C/C++

    ```java
    public class AreaOfCircle {
       public static void main(String[] args) {
    	  float PI = 3.14F; // PI is a constant
    	  float r = 0.0;
      	  System.out.print("Enter circle radius: ");
    	   r = UserInputReader.readFloat();
    	   System.out.println(“Circle area is " + PI * r * r);
      }
    }
    ```

    

  * **Stepper**: A variable stepping through values that can be predicted as soon as the succession starts.(increment or, i++)

    * Purpose: Goes through a sequence of values systematically

    ```java
    public class MultiplicationTable {
       public static void main(String[] args) {
    	int multiplier;
    	for (multiplier = 1; multiplier <= 10; multiplier++)
    		System.out.println(multiplier + " * 3 = "
    			+ multiplier * 3);
    	}
    }
    ```

    

  * **Most-recent holder**: A variable holding the latest value encountered in going through a succession of values. 

    * Most recent member of a group, or simply latest input value

      * e.g.: when asking the user for an input until input value is valid
      * s in the following example

      ```java
      public class AreaOfSquare {
         public static void main(String[] args) {
      	float s = 0.0;
      	while (s <= 0) {
      		System.out.print("Enter side of square: ");
      		s = UserInputReader.readFloat();
      	}
      	System.out.println(“Area of square is " + s * s);
      	}
      }
      ```

      

  * **Gatherer**: A variable accumulating the effect of individual values in going
    through a succession of values. 

    * Purpose: Accumulates values seen so far: accepts integers, then calculates mean
    * Variable sum is a gatherer

    ```java
    public class MeanValue {
        public static void main(String[] argv) {
    	int count=0;
    	float sum=0, number=0;
    	while (number != -999) {
    	   System.out.print("Enter a number, -999 to quit: ");
           // number is most recent holder
    	   number = UserInputReader.readFloat();
     	   if (number != -999) { sum = sum + number; count++; }
     	}
    	if (count>0) 
            System.out.println("The mean is " + sum / count);
       }
    }
    
    ```

    

  * **One-way flag**: A two-valued variable that cannot get its initial value once its value has been changed.

    * Purpose: serve as a Boolean variable (true or false)
    * Example: sum input numbers and report if any negative numbers

    ```java
    public class SumTotal {
       public static void main(String[] argv) {
    	int number=1, sum=0;
    	boolean neg = false;	//one-way flag
    	while (number != 0) {
    	    System.out.print("Enter a number, 0 to quit: ");
    	    number = UserInputReader.readInt(); sum += number;
    	   if (number < 0) neg = true;
    	}
    	System.out.println("The sum is " + sum);
    	if (neg) 
            System.out.println(“There were negative numbers.");
       }
    }
    
    ```

    

  * **Temporary**: A variable holding some value for a very short time only. 

    * Keep values that are only needed for very short period(e.g. separated by a few lines of code)

      - e.g.: output two numbers in size order, swapping if necessary

      ```java
      public class Swap {
         public static void main(String[] args) {
      	int number1, number2, tmp;
      	System.out.print("Enter num: ");
      	number1 = UserInputReader.readInt();
      	System.out.print("Enter num: ");
      	number2 = UserInputReader.readInt();
      	if (number1 > number2) {
      		tmp = number1;
      		number1 = number2;
      		number2 = tmp;
      	}
      	System.out.println(“Order is " + number1 + “," + number2 + ".");
         }
      }
      
      ```

      

  * **Organizer:** An array which is only used for rearranging its elements after
    initialization. (container)

    * An array[] for containing and rearranging elements
    * e.g.: input ten characters and output in reverse order

    ```java
    public class Reverse {
       public static void main(String[] args) {
    	char[] word = new char[10];	// organizer
    	char tmp; int i;
    	System.out.print("Enter ten letters: ");
    	for (i = 0; i < 10; i++) word[i] = UserInputReader.readChar();
    	for (i = 0; i < 5; i++) {
    		tmp = word[i];
    		word[i] = word[9-i];
    		word[9-i] = tmp;
    	}
    	for (i = 0; i < 10; i++) System.out.print(word[i]);
    	System.out.println();
      }}
    ```

    

  * **Transformation**: A variable that always gets its new value from the same calculation from value(s)of other variable(s). 

    * Purpose: Compute value in new unit
    * e.g.: `speed = distance/time`

    ```java
    public class Growth {
       public static void main(String[] args) {
    	float capital, interest; int i;
    	System.out.print("Enter capital (positive or negative): ");
    	capital = UserInputReader.readFloat();
    	for (i = 1; i <=10; i++) {		//stepper
    	     interest = 0.05 * capital;	//transformation
    	     capital += interest;		//gatherer
    	     System.out.println("After "+i+" years interest is "
    		+ interest + " and capital is " + capital);
    	}
       }
    }
    ```

    ![屏幕快照 2019-02-11 下午1.46.29](屏幕快照 2019-02-11 下午1.46.29.png)

### UML Class Diagram

* Class diagram: Used to visualize object-oriented classes and their relationships in our system

  ![image-20190211135617693](image-20190211135617693.png)

* Class linkages

  ![image-20190211135753054](image-20190211135753054.png)

  * Composition
    * A has B(Must/compulsory, i.e. B must be included)
    * Implementation: Class_A contains a fixed local variable links to Class_B
  * Aggregation 
    * A has B(B is Optional, can be included later)
    * Implementation: Class_A contains a changale local variable links to Class_B
  * Association
    * A uses B(may be as a parameter, can define B at runtime, more dynamic)
      * ***Class_A*** DO NOT contain a local variable links to ***Class_B*** 
      * ***Class_A*** uses ***Class_B*** as (input/output) ***Parameter*** directly.

* Example:

  ![image-20190211140103561](image-20190211140103561.png)

  ![屏幕快照 2019-02-11 下午2.02.08](屏幕快照 2019-02-11 下午2.02.08.png)

* Association & Mutiplicity

  ![image-20190211140418079](image-20190211140418079.png)

-------------



