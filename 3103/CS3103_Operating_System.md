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

    ![](/Users/zdh/Documents/GitHub/Notes/屏幕快照 2019-01-14 下午8.04.52.png)

* 