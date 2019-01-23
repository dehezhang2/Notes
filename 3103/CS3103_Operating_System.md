# CS3103 Operating System

----------

## Chapter 1,2 Computer System & Operating System Overview

--------

### Basic Elements

* Processor(Central Processing Unit)
  * 2 parts
    * Control unit : Control operation
    * Arithmetic & Logic Unit : perform data processing
  * Works repeatedly and continuously in cycles to execute instructions
* Main Memory(RAM/primary memory)
  * consists of a set of locations defined by sequentially numbered addresses
  * stores data and programs
  * volatile
* I/O Modules : moves data between the computer and the external environment(storage, communications equipment, terminals)
* System Bus : Provides for communication among processors, main memory, and I/O modules

### Instruction Execution

* A program consists of a set of instructions stored in memory

* 4 steps in a machine cycle(fetch and execute)
  * Processor reads (fetches) an instruction from memory
  * Processor interprets (decodes) the current instruction
  * Processor executes the instruction
  * Processor stores the result back to memory
* Registers : special memory locations **inside the processor** that can be accessed very fast
  * **PC**: hold the address of the instruction to be fetched next (incremented after each fetch)
  * Fetched instruction loaded into **IR**
  * **AC** : store execution result temporarily
  * **PSW(Program Status Word)** : contains execution status information
* Each instruction contains bits (*opcode*) specifying what action the CPU needs to take:
  * Processor-memory

  * Processor-I/O

  * data processing

  * control

  * 4 bits opcode for 16 instructions($2^4$), 12 bits left refer to a memory address

    * (0001): Load AC from memory
    * (0010): Store AC to memory
    * (0101): Add to AC from memory

    ![](屏幕快照 2019-01-18 下午3.41.03.png)

### Interrupts(New)

* **Interrupt** the **normal sequencing of the processor** by **other modules**

* types

  * Program: exception
  * Timer
  * I/O
  * Hardware failure

* provided to improve processor utilization

  * Most I/O devices are slower than the processor
  * Processor pauses to wait for device -> wasteful use of the processor

* Example

  * The solide vertical lines represent code segments

  * The dash lines represent the order of execution

  * I/O program includes: **label 4**(before execution, prepare output buffer); **Actual I/O command**(without interrupt, the program must wait and can only test whether the I/O instruction is end); **label 5**(after execution, may include set the flag that indicate the success or failure of the execution)

  * **If change write to read, you still have to wait, because before finish of reading, you don't have the data to be executed**

    ![](屏幕快照 2019-01-14 下午8.04.52.png)

    ![](屏幕快照 2019-01-14 下午8.04.59.png)

* Transfer of control via Interrupts

  * Interrupt suspends(暂停) normal sequence of execution(control given to the Interrupt Handler)
  * execution resumes when the interrupt processing is completed
  * **Important** : what could happen when the I/O operation takes much more time than executing the code segment 2 or 3 of the user program, i.e., the user program reaches the second WRITE call before the I/O operation called by the first one is completed: **processor** will wait for the last I/O opeartion, and generate an idle wait time

  ![](屏幕快照 2019-01-14 下午8.11.33.png)

  ![](屏幕快照 2019-01-14 下午8.40.09.png)

  * Hardware part: done automatically by hardware; Software part: need to be considered by OS programmers
  * PSW is register store the information of program execution(independent of **stack**)

  ![](屏幕快照 2019-01-14 下午8.43.32.png)

* Uniprogramming vs Multiprogramming

  * Uniprogramming: only one program is running at a given time
    * The processor spends a certain amount of time executing, until it reaches an I/O instruction; it must then wait until that I/O instruction concludes before proceeding
  * Multiprogramming: processor has more than one program to execute(**Enable interrupts**)

    * When **one job(A)** needs to wait for I/O, the processor can switch to the **other job(B,C)**.

      ![](屏幕快照 2019-01-14 下午8.51.43.png)

* Interrupt, multiprogramming and multiprocessing

  * **Interrupt**: save the time between the initialization and finalization of I/O operation by doing next instruction, but generate idle wait time when the second write instruction called before the first write completed
  * **Multiprogramming**: A lot of programs(not instructions) run at the same time, when one is in I/O operation(READ case which is not possible continue or idle time slot), the other do the calculation
  * **Multiprocessing**: A lot of processors run at the same time
    * When there is only one program to run, multiprogramming will not improve the performance by fill the I/O wait time, but using multiprocessing can divide one progress into many and run at the same time. 

### Memory Hierarchy

* Going down the hierarchy
  * decreasing cost per bit
  * Increasing capacity
  * Increasing access time(lower speed)
  * Decreasing frequency of access to the memory by the processor

* **Cache Memory**: Processor must access memory at least once per instruction cycle -> processor execution is limited by memory cycle time, but processor speed is much faster than memory access speed
  * Solution: copy information in use from slower to faster (but smaller) storage (cache) temporarily

  * checked first to determine if information is there

  * Principle of locality: Data which is required soon is often close to the current data. If data is accessed,
    then it’s neighbors might also be accessed in the near future.

  * **Tricky case** : 

  * Consider a memory system with the following parameters: 

     * Cache access time: 0.1 $\mu s $ 

     * Memory access time (time needed to load a 				    word into the cache): 1 $\mu s$ 

     * Suppose we ignore the time required for the processor to determine whether a word is in cache or memory. What is the ***hit ratio*** in order to have an average time to access a word no more than 50% greater than the cache access time?

        
       $$
       h*1+(1-h)*\color{red}{(1+0.1)}<=1.5
       $$
       

* Secondary Memory: Also known as storage devices
  * extension of main memory that provide large nonvolatile storage capacity
  * Used to store program and data files
  * Most commonly used: magnetic disks
    * Disk surface is logically divided into *tracks*, which are subdivided into *sectors*.
    * The disk controller determines the logical interaction between the device and the computer

### I/O Communication Techniques

* When the processor encounters an instruction relating to I/O , it executes that instruction by issuing a command to the appropriate I/O module

* Three techniques are possile

  * Programmed I/O

    ![](屏幕快照 2019-01-15 上午8.54.49.png)

  * Interrupt-driven I/O

    ![](屏幕快照 2019-01-15 上午8.55.05.png)

  * Direct memory access (DMA)

    ![](屏幕快照 2019-01-15 上午8.58.11.png)

  

### Operating System Objectives & Functions

* Definition of Operating System (OS)

  ![](屏幕快照 2019-01-15 上午10.30.37.png)

  * A program that control the execution of application programs
  * An **interface between application and hardware**
  * Main objectives of an OS
    * Convenience : Making a computer more **convenient to use**
    * Efficiency : Allowing computer **resources** to be used efficiently
    * Ability to evolve : Permitting effective development, testing and introduction of new system functions
      * hareware upgrade / new hardware
      * new services
      * fixes

* OS Servivces

  * Program developement(editors and debuggers)
  * Program execution(OS handles steps need to be performed to execute a program, i.e. instructions)
  * Access I/O devices(OS provides a uniform interface so that programmers can access I/O devices using simple reads and writes)
  * Controlled access to files(In the case of system with multiple users OS provides protection mechanisms to control access to the files)
  * System access(also for shared systems)
  * Error detection and response(OS must provide a response that clears the error condition with the least impact on running applications. )
  * Accounting(A good OS will collect usage statistics for various resources and monitor
    performance parameters such as response time)

* OS as resource manager

  * A computer is a set of resources for the movement, storage, and processing of data
  * OS is responsible for managing these resourses
    * how much processor time is to be devoted to the execution of a particular user program
    * controls the allocation of main memory
    * decides when an I/O device can be used by a program in execution
    * controls access to the use of files

* Major topics of OS

  ![](屏幕快照 2019-01-15 上午10.54.26.png)

----------------

## Chapter 3 Process Description and Control

-----------

* **Process states** which characterize the behaviour of processes
* **Data structure** used to manage processes
* OS use data structures to control process execution

-------------------------

### How are processes represented and controlled by the OS

* All modern OS rely on a model in which the execution of an application corresponds to the existence of one or more processes.
* Example: single-user systems such as Windows and mainframe system such as IBM’s mainframe OS, z/OS, are built around the ***concept of process***. 
* Process : A program in execution
  * An **instance of** a program running on a computer
  * The entity that can be assigned to and executed on a processor
  * A unit of activity characterized by the execution of a **sequence of instructions, a current state, and an associated set of system resources**
* Process Elements
  * Program code
  * Associated data needed by the program
  * Execution context of the program, containing all information the OS needs to manage the process
* Requirement of an OS
  * fundamental task: process management
    * Interleave(插入) the execution of multiple processes
    * Allocate resources to processes and protect the resources of each process from other processes
    * enable processes to share and exchange information (interprocess communication)
    * enable synchronization among processes
  * Example
    * Consider three processes being executed
    * Plus a ***dispatcher*** - a small program which switches the processor from one process to another
    * All are in memory
* Trace from processes' point of view
  * The behavior of an individual process can be characterized by listing the sequence of instructions that execute for that process: a *trace* of the process.