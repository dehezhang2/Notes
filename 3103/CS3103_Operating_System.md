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
* Processor: memory:I/O=1:few handreds:ten million
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

* **Cache Memory**: Processor must access memory at least **once per instruction cycle** -> processor execution is limited by memory cycle time, but processor speed is much faster than memory access speed

  * Solution: copy information in use from slower to faster (but smaller) storage (cache) temporarily

  * checked first to determine if information is there

  * **Principle of locality**: Data which is required soon is often close to the current data. If data is accessed,
    then it’s neighbors might also be accessed in the near future.

    * If it is, information used directly from the cache
    * If not, data copied to cache and used there

  * **Tricky case** : Consider a memory system with the following parameters: 

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

    * Good for simple and cheap product

    ![](屏幕快照 2019-01-15 上午8.54.49.png)

  * Interrupt-driven I/O

    ![](屏幕快照 2019-01-15 上午8.55.05.png)

  * Direct memory access (DMA)

    * need DMA module which is expensive

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
    * how much **processor time** is to be devoted to the execution of a particular user program
    * controls the **allocation of main memory**
    * decides when an **I/O device** can be used by a program in execution
    * controls **access to the use of files**

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

* All modern OS rely on a model in which the execution of an application corresponds to the existence of **one or more processes.**

* Example: single-user systems such as Windows and mainframe system such as IBM’s mainframe OS, z/OS, are built around the ***concept of process***. 

* Process :

  *  A program in execution
  * An **instance of** a program running on a computer
  * The entity that can be **assigned to** and **executed on a processor**
  * A unit of activity characterized by the execution of a **sequence of instructions, a current state, and an associated set of system resources**

* Process Elements

  * Program **code**
  * Associated **data** needed by the program
  * **Execution context** of the program, containing all **information the OS needs to manage the process**

* Requirement of an OS

  * fundamental task: process management

    * Interleave(插入) the execution of multiple processes(multiprogramming)
    * Allocate resources to processes and protect the resources of each process from other processes
    * enable processes to share and exchange information (interprocess communication)
    * enable synchronization among processes

  * Example

    <img src="image-20190125105129354.png" width="40%"/>

    * Consider three processes being executed
    * Plus a ***dispatcher*** - a small program which switches the processor from one process to another
    * All are in memory

* Trace from processes' point of view

  ![image-20190125105425393](image-20190125105425393.png)

  * The behavior of an individual process can be characterized by listing the sequence of instructions that execute for that process: a *trace* of the process.

* Trace from processor's point of view(6 instructions per process each time)

  ![image-20190125105610940](image-20190125105610940.png)

---------

### A flavour of creating a process in UNIX

* Creating Process in UNIX

  * A parent process can create a child process by means of the *system call*, `fork()` (return the id of the child process,if do not exist, return 0)
  * After creating the process, the OS can do one of the following, as part of the dispatcher(调度员) routine
    * Stay in the parent process
      * control returns to the point of the fork call of the parent
    * Transfer control to the child process
      * The child process begins executing at the same point in the code as the parent, namely at the return from the fork call
    * Transfer control to another process

  ![image-20190125110938704](image-20190125110938704.png)

  * `fork()` just create a child process copy every thing of parent process
    * but child process just run the codes after fork
    * `pid()` returns the id of child process in parent process
    * `getpid()` returns the id of current process
    * `getppid()` returns the id of parent process

-----------

### Process states which characterize the behaviour of processes

#### Two-State Process Model

![image-20190125111908290](image-20190125111908290.png)OS creates a new process and enters it into the system

* Process may be in one of two states: Running & Not-running

* Queuing Diagram: Processes that are not running are kept in some sort of queue, waiting for their turn to execute

![image-20190125111318389](image-20190125111318389.png)

* Process Birth and Death

  ![image-20190125111613239](image-20190125111613239.png)

* Five-State Process Model

  ![image-20190125111931505](image-20190125111931505.png)

  * Distinguish between blocked and ready state
  * While some processes in the Not Running state are ready to execute, **others may be blocked**(e.g., **waiting for an I/O operation to complete**, or timer interrupt) , while ready state represent process that **run out of its instructions for this turns** (timer interrupt)
  * Using Two Queues/Multiple Blocked Queues

  ![image-20190125112106945](image-20190125112106945.png)

  ![image-20190125112145701](image-20190125112145701.png)

* Suspended Processes

  * Processor is faster than I/O so **all** processes could be waiting for I/O -> processor could be idle most of the time

    * When there are **too many blocked processes in the main memory**, the speed of process will be too slow
    * OS swaps one of the blocked processes out on to disk to **free up more memory** and use processor on other processes

  * Blocked state becomes **suspend** state **when swapped to disk**

  * Distinguish between suspend state and blocked state(whether the process is in the main memory or not)

  * One suspend state

    ![image-20190125113832425](image-20190125113832425.png)

    ​	

    * Although each process in the suspend state was originally blocked on a particular event, when that event occurs, the process is not blocked and is potentially available for execution
    * 阻塞 VS 挂起(blocked vs. suspended)
    * 阻塞与挂起都是进程的状态，但他们有一些相似之处，也有一些区别，下面先对他们进行概述，再进行比较
      * 阻塞：正在执行的进程由于发生某时间（如I/O请求、申请缓冲区失败等）暂时无法继续执行。此时引起进程调度，OS把处理机分配给另一个就绪进程，而让受阻进程处于暂停状态，一般将这种状态称为阻塞状态。
      * 挂起：由于系统和用户的需要引入了挂起的操作，进程被挂起意味着该进程处于静止状态。如果进程正在执行，它将暂停执行，若原本处于就绪状态，则该进程此时暂不接受调度。
      * 共同点：
        * 进程都暂停执行
        * 进程都释放CPU，即两个过程都会涉及上下文切换
      * 不同点：
        * 对系统资源占用不同：虽然都释放了CPU，但阻塞的进程仍处于内存中，而挂起的进程通过“对换”技术被换出到外存（磁盘）中。
        * 发生时机不同：阻塞一般在进程等待资源（IO资源、信号量等）时发生；而挂起是由于用户和系统的需要，例如，终端用户需要暂停程序研究其执行情况或对其进行修改、OS为了提高内存利用率需要将暂时不能运行的进程（处于就绪或阻塞队列的进程）调出到磁盘
        * 恢复时机不同：阻塞要在等待的资源得到满足（例如获得了锁）后，才会进入就绪状态，等待被调度而执行；被挂起的进程由将其挂起的对象（如用户、系统）在时机符合时（调试结束、被调度进程选中需要重新执行）将其主动激活
      * 挂起和阻塞区别：
        * 挂起是一种主动行为，因此恢复也应该要主动完成。而阻塞是一种被动行为，是在等待事件或者资源任务的表现，你不知道它什么时候被阻塞，也不清楚它什么时候会恢复阻塞。
        * 阻塞（pend）就是任务释放CPU，其他任务可以运行，一般在等待某种资源或者信号量的时候出现。挂起（suspend）不释放CPU，如果任务优先级高，就永远轮不到其他任务运行。一般挂起用于程序调试中的条件中断，当出现某个条件的情况下挂起，然后进行单步调试。
      * sleep（）和wait（）函数的区别：
        * 两者比较的共同之处是：两个方法都是使程序等待多少毫秒。
        * 最主要区别是：sleep（）方法没有释放锁。而wait（）方法释放了锁，使得其他线程可以使用同步控制块或者方法。
        * sleep（）指**线程**被调用时，占着CPU不工作，形象的说明为“占着CPU”睡觉。（一个进程可能有多个线程）
          * sleep(2000)表示：占用CPU，程序休眠2秒。
          * wait(2000)表示：不占用CPU，程序等待2秒。

  * Two suspend states (blocked/suspend and ready/suspend)

    * Because block and suspend are 2 independent states(block: whether has interrupt; suspend: whether in the main memory)
    * May be there is a program waiting for user input, and at this time OS decide to move it outof the main memory

    ![image-20190125114715372](image-20190125114715372.png)

  * Reason for Process Suspension

    <img src="image-20190125114813156.png" width="100%">

------------

### Data structures used to manage process

* Processes and Resources: OS manages **the use of system resources by processes**

  ![image-20190125115213818](image-20190125115213818.png)

* Operating System Control Structures

  * For the OS to manage processes and resources, it must have information about the **current status of each process and resources**

  * Tables are constructed for each entity the OS manages

    ![image-20190125121059813](image-20190125121059813.png)

* Memory Tables

  * Memory tables are used to keep track of both main(real) and secondary(virtual memory)
  * Must include this information
    * **Allocation of main memory** to processes
    * **Allocation of secondary memory** to processes
    * **Protection attributes** of blocks of main or virtual memory such as which processes may **access certain shared memory regions**
    * Information needed to **manage virtual memory**

* I/O Tables

  * Used by the OS to **manage the I/O devices** and channels of the computer.
  * At any given time, an I/O device may be **available or assigned to a particular process.**
  * If an I/O operation is in progress, the OS needs to know
    * The **status of the I/O operation**
    * The **location in main memory being used as the source or destination of the I/O transfer**

* File Tables

  * These tables provide information about:
    * **Existence** of files
    * **Location** on secondary memory
    * **Current status**
    * other attributes.
  * Sometimes this information is maintained by a file management system

* Process Table

  * To manage and control a process, there is one entry for each process in the process table

    * Each entry points to a **process image**(进程投影) containing

    ![image-20190125121746307](image-20190125121746307.png)

* Process Control Block

  <img src="image-20190125122112852.png" width="30%">

  * Each process has associated with it a number of attributes that are used by the OS for process control.
  * The attributes are stored in a data structure called a ***process control block*** (PCB), created and managed by the OS.
  * It contains **sufficient information so that it is possible to interrupt a running process and later resume its execution.**

* Process Attributes : we can group the information in a PCB into three general categories:(**Process identification**, **Processor state information and Process control information**)

  * Process Identification: Each process is assigned a unique numeric identifier. (`pid()`)

    * Many of the tables controlled by the OS may use process identifiers to **cross-reference process tables**(relationship relation), e.g., memory tables may be organized to provide **a map of main memory with an indication of which process is assigned to each region**(process ID -> memory block)
    * When processes **communicate with one another**, the process identifier informs the OS of the **destination of a particular communication**
    * When processes are allowed to create other processes, identifiers **indicate the parent and descendants** of each process

  * Process State Information: Consists of processor registers' content

    * User-visible registers
    * **Control and status** registers
      * Program counter: address of the next instruction
      * Program status word(PSW)
        * Condition codes: –result
          of the **most recent arithmetic or logical operation** (e.g., sign, zero, carry,equal, overflow)
        * Status information: e.g. **interrupt enabled/disabled flags, execution mode**
      * Stack pointers

  * Process Control Infromation: The additional information needs by the OS to control and coordinate the various active processes

    * Process state
    * Priority
    * Scheduling-related info
    * Waiting event 
    * Data structing

  * Process List Structures： The queuing structure could be implemented as linked lists of PCBs in which pointers can be stored in the PCBs (structuring information)

    ![](屏幕快照 2019-01-25 下午12.40.59.png)

* Structure of Process Images in Virtual Memory![image-20190125124220632](image-20190125124220632.png)

* Role of the Process Control Block

  * Most important data structure in an OS
    * contains all of the information about a process that is needed by the OS
    * **Read and/or modified** by virtually every module in the OS such as scheduling, resource allocation, interrupt processing and performance monitoring
    * Defines the state of the OS
  * Requires protection, which is difficult
    * A faulty routine could damage PCBs, which could destroy the OS's ability to manage the affected processes
    * Any design change to the PCB could affect many modules of the OS

--------

### Ways in which the OS uses these data structures to control process execution

* Modes of Execution

  * Most processors support at least two modes of execution to protect the OS and key OS tables from interference by user programs.
  * User mode
    * Less-privileged mode
    * User programs typically execute in this mode
  * System mode (control mode or kernel mode)
    * More-privileged mode
    * *Kernel* of the operating system (central module of an OS)
      * Loads first when the system starts
      * Resides in memory (in a protected area) all the time

* Typical Functions of an OS Kernel

  ![image-20190125124545437](image-20190125124545437.png)

* Process Creation: Once the OS decides to create a new process, it:

  * **Assigns a unique process identifier** and adds a new entry to the process table
  * **Allocates space** for the process (process image)
  * Initializes process control block
  * Sets up appropriate **linkages such as putting the new process** in the Ready list
  * Creates or expands other data structures such as an accounting file for performance assessment

* Process Switching

  * When CPU switches to another process, the system must **save the state of the old process** and **load the saved state for the new process** (to be described).

  * *Process-switch* time is considered as **overhead** (the system does no useful work while switching), so several issues are important

    * What events trigger a process switch: A process switch may occur any time that OS has **gained control from the currently running process**. Possible events giving OS control are:

      | **Mechanism**                   | **Cause**                                                    | **Use**                                          |
      | ------------------------------- | ------------------------------------------------------------ | ------------------------------------------------ |
      | ***Interrupt***                 | External to the execution of the  current instruction, e.g., clock interrupt, I/O   interrupt. | Reaction to an asynchronous   external event     |
      | ***Trap***                      | Associated with the execution of the   current instruction, e.g., illegal file   access | Handling of an error or an exception   condition |
      | ***System   /supervisor call*** | Explicit request, e.g., file open                            | Call to an operating system function             |

    * What must the OS do to the various data structures to achieve such a process switch?(steps in a process switch)

      ![image-20190125125613564](image-20190125125613564.png)

      * Save context of processor including program counter and other registers
      * Update the PCB of the process currently in the Running state
      * Move the **PCB of this process to appropriate queue**- ready; blocked;ready/suspend
      * Select another process for execution
      * Update the PCB of the process for execution
      * Update memory management data structures
      * **Restore** context of the processor to that which existed at the time the selected process was **last switched out**

  * Mode Switching

    * The occurrence of an **interrupt** does not necessarily mean a process switch
    * It is possible that, after the processor switches from user mode to kernel mode in order to **execute the interrupt handler** (which may include privileged instructions), the currently running process will resume execution.
    * In such a *mode switching* case, only need to save / restore the processor state information. 

----------------

### Discuss process management in UNIX

* System processes run in kernel mode 

  * executes operating system code to perform administrative and housekeeping functions
* User processes
  * operate in user mode to execute user programs and utilities

  * operate in kernel mode to execute instructions that belong to the kernel

  * enter kernel mode by issuing a system call, when an exception is generated, or when an interrupt occurs

    ![image-20190201145410802](image-20190201145410802.png)

  ![image-20190201172404002](image-20190201172404002.png)

* Process Creation in Unix

  * Process creation is by means of the kernel system call, **fork( )**

  * This causes the OS, in kernel mode, to:

    1. Allocate a slot in the process table for the new process.

    2. Assign a unique process ID to the child **process**.

    3. **Make a copy of the process image of the parent**, with the exception of any shared memory.

    4. Increment counters for any files owned by the parent, to reflect that an additional process now also owns those files.

    5. Assign the child process to the Ready to Run state.

    6. Return the ID number of the child to the parent process, and a 0 value to the child process.
    7. Their data are independent with each other even if they has a same variable name 

  * After creation (different choices **for OS**, different with the explicit system call by user, brecause it means whose **next instruction to be called**)

    * Stay in the parent process: Control returns to ***user mode*** at the point of the fork call of the parent
    * Transfer control to the child process: The child process **begins executing at the same point in the code as the parent**, namely at the return from the fork call
    * Transfer control to another process: Both parent and child are left in the ***Ready to Run*** state


--------

## Chapter 04 Threads

-----

### Threads: Resource ownership and execution

* Processes and Threads
  * Resource ownership: 
    * A process is allocated ownership of resources including a virtual address space to hold **process image**(user data, user program, stack, PCB)
    * OS performs a protection function to prevent unwanted interference between processes with respect to resource
  * Dispatching/scheduling/execution
    * The execution of a process follows an **execution path** that may be **interleaved with other processes**
    * A process has an **execution state(Running, Ready,etc) and a dispatching priority**, and is the entity that is **scheduled and dispatched by the OS**

* Multithreading
  * These two characteristics can be treated independently by the OS
    * The ==unit of dispatching== is referred to as a ***thread*** or lightweight process
    * The unit of ==resource ownership== is referred to as a ***process*** or task
  * ***Multithreading*** is the ability of an OS to support multiple, ==concurrent paths of execution== within **a single process**.

![image-20190210183331621](image-20190210183331621.png)

* Single-threaded Approaches: A single thread of execution per process(concept of thread is not recognized)

  * MS-DOS supports a ==single-user process and a single thread==
  * Some variants of UNIX support multiple user processes but only support one thread per process

* Multithreaded Approaches

  * A **Java run-time environment** is a system of one process with multiple threads.
  * The use of multiple processes, each of which supports multiple threads are found in Windows, Solaris, and many modern versions of UNIX.

* Process vs. Thread

  * Process (in OS): 

    * A **unit of resource allocation**: a virtual address space that holds the ***process image*** (code + data + stack + PCB)
    * A **unit of protection**: protected access to processors, other processes (for inter-process communication), files, I/O resources

  * Thread(in Process):

    * An execution **state** (running, ready, etc.)
    * A saved thread **context** when not running
    * An execution **stack**
    * Some per-thread **static storage** for local variables
    * Access to the memory and resources of its process, **shared by all threads** in that process

    ![image-20190210184018024](image-20190210184018024.png)

  * One way to view a thread is as an **independent program counter operating within a process to execute different part of instructions in the main memory** 

    ```c++
    #include <pthread.h>
    int g = 0;
    void *myThreadFun(void *vargp){
        long myid = *(long*)vargp;
        int s = 0;
        ++s; ++g;
        printf("Thread ID: %ld, local: %d, global: %d\n"
              , myid, ++s, ++g);
    }
    
    int main(){
        pthread_t tid;
        for(int i=0;i<3;i++)
        	pthread_create(&tid,NULL,myThreadFun,(void*)i);
        pthread_exit(NULL);
        return 0;
    }
    ```

    

* **Activities Similar to Processes**: Similar to processes, threads have *execution states* and need to *synchronize* with one another.

  * Execution states
    * Reminder: In an OS that supports threads, scheduling and dispatching is done on a thread basis.
    * Most of the **state information dealing with execution** is maintained in **thread-level** data structures.
    * The key states for a thread are: Running, Ready, Blocked.
    * Some states are at process-level
      * Suspending a process involves ==suspending all threads== of the process because they share the address space.
      * ==Termination of a process terminates all threads within the process==.
  * Threads need to **synchronize** with one another so that they **don't interfere with each other or corrupt data structures**
    * All threads of a process share the **same address space and other resources**.
    * ==Any alteration of a resource by one thread affects the other threads in the same process.==

* Multithreading on a Uniprocessor(单处理器): Mutiprogramming enables the interleaving(插入) of multiple threads within multiple processes

  ![image-20190210215255338](image-20190210215255338.png)

* Examples of using Thread

  * Foreground and background work: 

    In a word processor, a thread for interacting with the user, one thread for background editing, and a 3rd thread to do periodic backup asynchronously

  * Asynchronous processing: 

    In a Web server, multiple threads can work independently and simultaneously, such as issuing SQL queries and invoking Web services, to gather information that are required to build a Web response page

  * Speed of execution

    In computer graphics, matrix data can be divided and distributed into multiple threads to be calculated in parallel (on multiple cores)

* *Benefits of Threads*: If an application is implemented as **a set of related units of execution**, it is far more efficient to do so as a collection of threads rather than a collection of separate processes. Reasons include: 

  * less time to **create & terminate & switch** new thread than a process
  * Ehance efficiency in communication because threads within the same process ==share memory and files==, they can ==communicate== with each other ==without invoking the kernel==

-------

### Categories of thread implementation

* User Level Thread(ULT): All thread management is done within the application by calling a threads library

  ![image-20190210220658787](image-20190210220658787.png)

  * The application and its threads are allocated to a single process managed by the kernel
  * The kernel is not aware of the existence of threads
  * Kernel scheduling is done on a process basis
  * e.g.: GNU Portable Threads
  * Pros: 
    * Process does not switch to the kernel mode to do thread management -> saves the overhead of two mode switches
    * Scheduling can be application specific
    * Can run on ==any OS== because the threads library is a set of application-level functions(already based on the OS)
  * Cons: 
    * Only a single thread within a process can execute at a time -> a multithreaded application cannot take advantage of multiprocessing(processor just for one process's threads)
    * When a ULT executes a blocking system call, all of the threads within the process are blocked

* Kernel level Thread(KLT), also called(kernel-supported threads or lightweight processes): Thread management is done by the kernel

  ![image-20190210221107012](image-20190210221107012.png)

  * No thread management done by application, just an **API to the kernel thread facility**(服务)
  * Each user-level thread is mapped to a kernel-level thread
  * Kernel maintains context information for the whole process ==and individual threads within the process==.
  * Scheduling is done ==on a thread basis==.
  * e.g. : Windows, Linux
  * time comparation for three different kinds of the execution modes(for uni-processor)

  ![image-20190210222123084](image-20190210222123084.png)

  * Pros:
    * The kernel can simultaneously schedule multiple threads from the same process onto multiple processors.
    * If one thread in a process is blocked, the kernel can schedule another thread of the same process.
    * Kernel routines themselves can be  multithreaded.
  * Cons:
    * The transfer of control from one thread to another within the same process requires a mode switch to the kernel.(conversion overhead)
    * Managing KLTs is slower than ULTs.
    * KLT implementation needs ==OS support==.

* Combined Approach: **m-to-n hybrid** implementation

  * ![image-20190210222324632](image-20190210222324632.png)Application creates *m* ULTs.
  * OS provides pool of *n* KLTs(n processors to manage).
  * Multiple ULTs are mapped onto a ==smaller or equal number of KLTs==.
  * Multiple threads within the same application can run in parallel on multiple processors.
  * A blocking system call need not block the entire process.
  * Example: Solaris

--------

### Thread library (POSIX Threads(Pthreads)) [src](https://computing.llnl.gov/tutorials/pthreads)

------

* Thread Libraries: Provide programmer with API (application program interface) for creating
  and managing threads.

  * Three main thread libraries are in use today:
    * POSIX Pthreads
    * Win32
    * Java
  * UNIX and Linux systems often use Pthreads.

* Pthreads(POSIX Threads)

  * Historically, hardware vendors(卖主) have implemented their own proprietary(专卖) versions of threads.
  * For UNIX systems, a standardized C language ***threads programming interface*** has been specified by the IEEE POSIX 1003.1c standard (*Portable Operating System Interface*)*.*
  * Implementations that adhere(依附) to this standard are referred to as **POSIX threads**, or **Pthreads**.
  * Most hardware vendors now offer Pthreads in addition to their proprietary API's.

* What are Pthreads?

  * Pthreads are defined as a set of C language programming types and procedure calls
  * Implemented with a `pthread.h` header/include file and a thread library
  * This makes it easy for programmer to develop *portable* threaded applications

* The Pthreads API: The subroutines which comprise the Pthreads API can be informally grouped into four major groups: 

  * ***Thread management*** 

    * Create, detach(分开), join 
    * Set/query thread attributes

  * ***Mutexes*** : Deal with synchronization via a “***mutex***” (mutual（相互） exclusion)

  * ***Condition variables*** : Address communications between threads that share a mutex

  * ***Synchronization*** : Manage read/write locks and barriers

  * Some of the thread-management function calls

    ![image-20190210223323989](image-20190210223323989.png)

  * Naming conventions: All identifiers in the threads library begin with `pthread`

* Multithreading Consequences: Because threads within the same process share resources

  * Changes made by one thread to shared system resources (such as closing a file) will be seen by all other threads
  * Two pointers having the same value point to the same data
  * Reading and writing to the same memory locations is possible
  * No guarantee as to the order that threads will run
  * Therefore requires ==explicit *synchronization* by the programmer==

-------------

## Chapter 05 Concurrency: Mutual Exclusion and Synchronization

--------

### Principles of Concurrency

* OS design is concerned with the management of processes and threads in different systems

  * Multiprogramming: Multiple processes, one core
  * Multiprocessing: Multiple processes, multiple cores (shared memory)
  * Distributed Processing: Multiple process, multiple nodes (distributed memory)

* Processes not only interleave(插入) but also overlapped on multi-processors

  ![image-20190217190445211](image-20190217190445211.png)

* Principles of Concurrency(an assumption): ***Interleaving*** and ***overlapping*** can be viewed as examples of **concurrent(同时发生) processing** and present the same problems

  * The relative speed of execution of processes cannot be predicted.
    * depends on activities of other processes
    * the way the OS handles interrupts
    * scheduling policies of the OS

* Difficulties of Concurrency

  * Sharing of global resources: global variables(may be changed)
  * Difficult for OS to manage the allocation of resources optimally: Multiple
    processes may request use of the same resource.
  * Difficult to locate programming errors: Results are not deterministic and reproducible

* **Race Condition**: Occurs when multiple processes or threads read and write shared data items

  * Final result depends on how the execution of instructions in the multiple processes interleaves

  * "Loser" of the race is the process that updates last and will determine 

  * e.g.: P1 P2 are 2 threads can access X

    ![image-20190217192559555](image-20190217192559555.png)

    ![image-20190217192623378](image-20190217192623378.png)

* OS Concerns: What design and management issues are raised by the existence of concurrency?

  * keep track of various processes
  * allocate and de-allocate resources for each active process; multiple processes want access to the same resource
  * protect the data and physical resources of each process against interference by other processes
  * **ensure that a process and its output must be independent of the speed at which its execution is carried out relative to the speed of other concurrent processes**

* Resouce Competition

  * Concurrent processes come into conflict when they are competing for use of the same resource such as I/O devices, memory, and processor time.
  * Three control problems must be faced:
    * **Need for mutual exclusion**
    * Deadlock
    * Starvation

### Mutual Exculsion

* Mutual Exculsion

  - The problem concerns a group of processes which need access to some resource that **cannot be used simultaneously by more than one single process.**
  - Control of competition involves the OS because it is the OS that allocates resources. 

  - The processes themselves also need to be able to express the requirement for mutual exclusion.

  - **Critical Section**: The piece of code within a process that accesses a shared resource (data structure or device) that must **not** be concurrently accessed by other processes.
  - It is important that only one program at a time be allowed in its critical section. 

* 

* 

### Semaphores

### IPC - Message Passing

### Readers/Writers Problem

--------

