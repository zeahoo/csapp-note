# A Tour of Computer Systems

## 1.1 Information Is Bits + Context

The source program is a sequence of bits, each with a value of 0 or 1, organized in 8-bit chunks called bytes.

## 1.2 Programs Are Translated by Other Programs into Different Forms

The translation is performed in the sequence of four phases:
1. Preprocessing phase. Read the contents of system header file and insert it directly into the program text.
2. Compilation phase. Translate the text file (modified source program hello.i) into text file hello.s(contain assembly-language program).
3. Assembly phase. Translate hello.s into machine-language instructions, packages them in a relocatable object program.
4. Linking phase. Handling merging separate percompiled objects in a file.

## 1.3 It Pays to Understand How Compilation Systems Work

Reason to understand how compilation systems work:
1. Optimizing program performance.
2. Understanding link-time errors.
3. Avoiding security holes.

## 1.4 Processors Read and Interpret Instructions Stored in Memory

### 1.4.1 Hardware Organization of a System

#### Buses.
Buses carry bytes of information back and forth between the components. They are typeically designed to transfer ﬁxed-sized chunks of bytes.
#### I/O Devices. 
System’s connection to the external world.
#### Main Memory.
A temporary storage device that holds both a program and the data.
#### Processor.
CPU is the engine that interprets (or executes) instructions stored in main memory.

A processor repeatedly executes the instruction pointed at by the program counter and updates the program counter to point to the next instruction.

The processor reads the instruction from memory pointed at by the program counter (PC), interprets the bits in the instruction, performs some simple operation dictated by the instruction, and then updates the PC to point to the next instruction.

CPU carry out at the request of an instruction:
+ Load
+ Store
+ Operate
+ Jump

### 1.4.2 Running the hello Program

As we type the characters “./hello” at the keyboard, the shell program reads each one into a register, and then stores it in memory.

When we hit the enter key on keyboard, the shell loads the executable file by executing a sequence of instructions that copies the code and data from disk to main memory.

Using direct memory access(DMA), the data travels directly from disk to main memory without passing through the processor.

Once the object file are loaded into memory, the processor start to execute the machine-language instructions in main function.Instructions copy the bytes from memory to the register file, and from these to display device, then displays on the screen.

## 1.5 Caches Matter

An L1 cache on the processor chip holds tens of thousands of bytes and can be accessed nearly as fast as the register ﬁle.

A larger L2 cache with hundreds of thousands to millions of bytes is connected to the processor by a special bus. It might take 5 times longer for the process to access the L2 cache than the L1 cache, but this is still 5 to 10 times faster than accessing the main memory. 

The L1 and L2 caches are implemented with a hardware technology known as static random access memory (SRAM).

Application programmers who are aware of cache memories can exploit them to improve the performance of their programs by an order of magnitude.

## 1.6 Storage Devices Form a Hierarchy

Memory hierarchy move from the top of the hierarchy to the bottom, the devices become slower, larger, and less costly per byte.

## 1.7 The Operating System Manages the Hardware

The operating system as a layer of software interposed between the application program and the hardware.

Operating system has two primary purposes:
1. To protect the hardware from misuse by runaway applications.
2. To provide applications with simple and uniform mechanisms for manipulating complicated and often wildly different low-level hardware devices.

Fundamental abstractions:
1. Files are abstractions for I/O devices.
2. Virtual memory is an abstraction for both the main memory and disk I/O devices.
3. And processes are abstractions for the processor, main memory, and I/O devices.

### 1.7.1 Processes

A process is the operating system’s abstraction for a running program.

The operating system performs this interleaving with a mechanism known as context switching.

The operating system keeps track of all the state information.

When the operating system decides to transfer control from the current process to some new process, it performs a context switch by saving the context of the current process, restoring the context of the new process, and then passing control to the new process.

1. The operating system saves the shell’s context, creates a new hello process and its context.
2. Then passes control to the new hello process.
3. After hello terminates, the operating system restores the context of the shell process and passes control back to it, where it waits for the next command line input.

### 1.7.2 Threads

A process as having a single control ﬂow, in modern systems a process can actually consist of multiple execution units, called threads, each running in the context of the process and sharing the same code and global data.

Threads is earsier to share data between multiple threads than between multiple processes, and because threads are typically more efﬁcient than processes.

### 1.7.3 Virtual Memory

Virtual memory is an abstraction that provides each process with the illusion that it has exclusive use of the main memory.

The virtual address space seen by each process consists of a number of welldeﬁned areas:

#### Program code and data

This is a fixed address of all processes, areas are initialized directly from the contents of an executable object ﬁle.

#### Heap

The heap expands and contracts dynamically at run time.

#### Shared libraries

#### Stack

Stack uses to implement function calls.Each time we call a function, the stack grows. Each time we return from a function, it contracts.

### Kernel virtual memory

This part is always resident in memory.

### 1.7.4 Files

Every I/O device, including disks, keyboards, displays, and even networks, is modeled as a ﬁle.

## 1.8 Systems Communicate with Other Systems Using Networks

Modern systems are linked to other systems by networks. The network can be viewed as just another I/O device.

## 1.9 Important Themes

### 1.9.1 Concurrency and Parallelism

+ Concurrency. Do more
+ Parallelism. Use concurrency to do faster.

#### Thread-Level Concurrency

This form of concurrency allows multiple users to interact with a system at the same time, such as when many people want to get pages from a single Web server.

#### Instruction-Level Parallelism

pipelining execute an instruction are partitioned into different steps and the processor hardware is organized as a series of stages, each performing one of these steps. The stages can operate in parallel, working on different parts of different instructions.

#### Single-Instruction, Multiple-Data (SIMD) Parallelism

### 1.9.2 The Importance of Abstractions in Computer Systems

The virtual machine, providing an abstraction of the entire computer, including the operating system, the processor, and the programs.