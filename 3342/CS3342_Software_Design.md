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
  * Process defines tasks and activities within a schedule
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

* **Waterfall Model**: Follows a systematic, sequential approach to SW development that begins at the system level and progresses through analysis, design, code and testing.

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
      * RAD will fail if we don’t have strong and skillful teams

* Evolutionary(演变) Process Models

  * **Specification,development and validation** activities are carried out *concurrently*(同时) with *rapid feedback* *across
    these activities*
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
    * Build the prototype by focusing on what will be seen by the user.
    * Use the prototype to show the user and help refining requirements.
    * Better communication
    * Advantage
      * Prototype can serve as a way for identifying requirements.
      * It is developed very quickly.
    * Disadvantage
      * Customer might think that the prototype is the final product and forget the lack of
        quality i.e. PERFORMANCE, RELIABILITY.
    * **When to use?**: 
      * When the customer define general objectives for the SW but does NOT identify details about INPUT, OUTPUT, or processing requirements.
      * The developer is unsure of the efficiency of an algorithm, human machine interaction, etc
  * Spiral Model
    * Iterative (like Prototype) and controlled (like waterfall)
    * Software is developed using evolutionary releases
    * Complexity increase with each release
    * A spiral process rather than as a sequence of activities with backtracking
    * *Each loop* in the spiral represents *a phase in the process*. 
    * *No fixed phases* such as req. specification or design - loops in the spiral are chosen depending on what is required—*more flexible*
    * Emphasize risk analysis and management (Risks are explicitly assessed and resolved throughout the process)

* The Spiral Model

