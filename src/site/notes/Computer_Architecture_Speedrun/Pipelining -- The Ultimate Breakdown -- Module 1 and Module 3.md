---
{"dg-publish":true,"permalink":"/computer-architecture-speedrun/pipelining-the-ultimate-breakdown-module-1-and-module-3/","title":"Pipelining -- Computer Architecture","tags":["Semester-4"],"created":"2025-03-06T18:33:20.305+05:30"}
---


 
---

# Index 

These are links to different sections within the note, won't work in pdf form.

[[#Module 1]]

1. [[#What is a pipeline?]]
2. [[#Design of a basic pipeline]]
3. [[#Performance measuring of a pipeline]]
4. [[#Pipeline dependencies/ Hazards]]
5. [[#Types of Pipeline]]
6. [[#Pipeline optimization techniques]]
7. [[#Compiler Techniques for improving performance in the pipeline]]

[[#Module 3]]

[[#Instruction level parallelism]]
[[#1. Superscalar architecture]]
[[#2. VLIW architecture]]
[[#3. Superpipelined architecture.]]
[[#Difference between all the architectures.]]

---

# Module 1

## What is a pipeline?

Pipelining is a process of the arrangement of the hardware elements of the CPU such that it's overall performance is increased. Simultaneous execution of more than one instruction takes place in a pipelined processor.

---
# Design of a basic pipeline

1. In a pipelined processor, a pipeline has two ends, an *input end* and the *output end*. Between these ends there are *multiple stages/segments* such that *the output of one stage is connected to the input of the next stage* and each stage performs a specific operation.
2. Interface registers are used to ==hold the intermediate output between two stages==. These interface registers are also called latch or buffer.
3.  All the stages in the pipeline along with the interface are controlled by a common clock.

---

# Performance measuring of a pipeline

Performance of a pipeline is measured using two metrics, *throughput* and *latency*.

## 1. Throughput

1. It measures the ==number of instructions per unit time==.
2. It represents overall processing speed of pipeline.
3. Higher throughput indicates processing speed of pipeline.
4. This is calculated as : *"Number of instructions executed"* / *execution time*
5. Throughput is influenced by pipeline length, clock frequency, efficiency of instruction execution.
## 2. Latency

1. It measures the ==time taken for a single instruction to complete it's execution==.
2.  It represents delay or time it takes for an instruction to pass through pipeline stages.
3.  ==Lower latency indicates better performance==.
4. It is calculated as : *Execution Time* / *Number of instructions executed*
5. It is influenced by *pipeline length*, *depth*, *clock cycle*, *instruction dependencies* and ==*pipeline hazards*.==

---

# Pipeline dependencies/ Hazards

1. Data Dependency
2. Structural Dependency
3. Control Dependency

These dependencies introduce *stalls* in the pipeline.
A *stall* is a cycle in the pipeline without new input.

---

# Structural Dependency.

This dependency exists due to ==resource conflicts in the pipeline==.

The *resource conflict* is a situation in which, more than one instruction tries to access the same resource in the same cycle.

A *resource* can be a *register*, *memory* or *ALU*.

As shown in the instruction cycle below :

![Pasted image 20240612094237.png](/img/user/Images/Pasted%20image%2020240612094237.png)


In this scenario, instructions *I1* and *I4* are trying to access the same resource *MEM (memory)* in the same cycle which causes a *conflict*. The instruction needs to be put on hold till the resource is available again. This unit period puts a stall in the pipeline as shown in the picture below:

![Pasted image 20240612094628.png](/img/user/Images/Pasted%20image%2020240612094628.png)

Here *I4* has to wait till 3 clock cycles to access *MEM* again.

## Solution for the structural dependency

To minimize structural dependency, we use a hardware mechanism called =="Renaming"==. 

According to Renaming:

1. We divide the memory into independent modules, which is used to store instructions and data separately, called Code Memory (*CM*) and Data Memory (*DM*). 
2. *CM* will contain all instructions and *DM* will contain all the operands (or variables).

![Pasted image 20240612095104.png](/img/user/Images/Pasted%20image%2020240612095104.png)

---
## Control Dependency (BRANCH Hazards)

This type of dependency occurs during the transfer of control instructions such as BRANCH, CALL, JMP, etc.

On many architectures, the processor will not know the target address, of these instructions when it needs when it needs to insert the new instruction into the pipeline. Due to this, unwanted instructions are fed into the pipeline.

For example, take the following instruction sequence :

![Pasted image 20240612210907.png](/img/user/Images/Pasted%20image%2020240612210907.png)

Here the target address (250) is only known after the IO stage.

![Pasted image 20240612211158.png](/img/user/Images/Pasted%20image%2020240612211158.png)

## Solution for the Control dependency

We introduce a delay in the pipeline.

(Temporary solution)

![Pasted image 20240612211937.png](/img/user/Images/Pasted%20image%2020240612211937.png)

---
# Data Hazards

Data hazards occur when instructions that exhibit data dependence, modify data in different stages of a pipeline. Hazard cause delays in the pipeline.

There are mainly three types of data hazards:

1) RAW (Read after Write) [Flow/True data dependency]
2) WAR (Write after Read) [Anti-Data dependency]
3) WAW (Write after Write) [Output data dependency]

For example:

 Let there be two instructions I and J, such that J follow I. Then:
 
- Instruction depend on result of prior instruction still in the pipeline.
- It can occur among the operands in the instruction at the pipeline stages.
- It occur when instructions read or write registers that are used by other instructions.
- - RAW hazard occurs when instruction J tries to read data before instruction I writes it. Eg: I: R2 <- R1 + R3 J: R4 <- R2 + R3
- WAR hazard occurs when instruction J tries to write data before instruction I reads it. Eg: I: R2 <- R1 + R3 J: R3 <- R4 + R5
- WAW hazard occurs when instruction J tries to write output before instruction I writes it. Eg: I: R2 <- R1 + R3 J: R2 <- R4 + R5

---
# Exceptions and Interrupts

Exceptions and interrupts are *unexpected events which will disrupt the normal flow of execution of instructions* that is currently being executed by the processor.

An exception is an *event from within the processor*.

An interrupt is an *event from outside the process*.


Whenever an exception/interrupt occurs, the hardware starts executing the code that performs an action in response to the exception. This may involve killing a process, outputting an error message, or *horribly crashing the entire computer system by initiating a ==BLUE SCREEN OF DEATH==* and *halting the CPU* 

## Exception and Interrupt Handling

Whenever an exception or interrupt occurs, *execution transitions from user mode to kernel mode* where the exception or interrupt is handled. In detail, the following steps must be taken to handle an exception or interrupts.

While entering the kernel, *the context (values of all CPU registers) of the currently executing process must first be saved to memory*. The kernel is now ready to handle the exception/interrupt:

1. Determine the cause of the exception/interrupt.
2. Handle the exception/interrupt.

When the exception/interrupt have been handled the kernel performs the following steps:

1. Select a process to restore and resume.
2. Restore the context of the selected process.
3. Resume execution of the selected process.


A detailed example (==read this only if you have time==) :

The exception/interrupt handler uses the same CPU as the currently executing process. When entering the exception/interrupt handler, the values in all CPU registers to be used by the exception/interrupt handler must be saved to memory. The saved register values can later restored before resuming execution of the process.

The handler may have been invoked for a number of reasons. The handler thus needs to determine the cause of the exception or interrupt. Information about what caused the exception or interrupt can be stored in dedicated registers or at predefined addresses in memory.

Next, the exception or interrupt needs to be serviced. For instance, if it was a keyboard interrupt, then the key code of the key press is obtained and stored somewhere or some other appropriate action is taken. If it was an arithmetic overflow exception, an error message may be printed or the program may be terminated.

The exception/interrupt have now been handled and the kernel. The kernel may choose to resume the same process that was executing prior to handling the exception/interrupt or resume execution of any other process currently in memory.

The context of the CPU can now be restored for the chosen process by reading and restoring all register values from memory.

The process selected to be resumed must be resumed at the same point it was stopped. The address of this instruction was saved by the machine when the interrupt occurred, so it is simply a matter of getting this address and make the CPU continue to execute at this address.

---

# Types of Pipeline

1. Instruction pipeline
2. Arithmetic pipeline

## 1. Instruction Pipeline 

An instruction pipeline *receives sequential instructions from memory while prior instructions are implemented in other portions*. Pipeline processing can be seen in both the data and instruction streams

Pipeline processing can happen not only in the data stream but also in the instruction stream. To perform tasks such as *fetching, decoding and execution of instructions*, most digital computers with complicated instructions would require an instruction pipeline.

In general, each and every instruction must be processed by the computer in the following order:

1. Fetching the instruction from memory

2. Decoding the obtained instruction

3. Calculating the effective address

4. Fetching the operands from the given memory

5. Execution of the instruction

6. Storing the result in a proper place

Each step is carried out in its own segment, and various segments may take different amounts of time to process the incoming data. Furthermore, there are occasions when multiple segments request memory access at the very same time, requiring one segment to wait unless and until the memory access of another is completed.

A *four-segment instruction pipeline* unifies two or more distinct segments into a single unit. For example, the decoding of the instruction and the calculation of the effective address can be merged into a single segment.

![Pasted image 20240613081912.png](/img/user/Images/Pasted%20image%2020240613081912.png)


A four-segment instruction pipeline is illustrated in the block diagram given above. The instructional cycle is divided into four parts:

### Segment 1

The implementation of the instruction fetch segment can be done using the FIFO or first-in, first-out buffer.

### Segment 2

In the second segment, the memory instruction is decoded, and the effective address is then determined in a separate arithmetic circuit.

### Segment 3

In the third segment, some operands would be fetched from memory.

### Segment 4

The instructions would finally be executed in the very last segment of a pipeline organization.

---

## 2. Arithmetic Pipeline

An arithmetic pipeline *separates a given arithmetic problem into subproblems that can be executed in different pipeline segments*. It’s used for multiplication, floating-point operations, and a variety of other calculations.

Arithmetic Pipelines are commonly used in various high-performance computers. They are used in order to implement floating-point operations, fixed-point multiplication, and other similar kinds of calculations that come up in scientific situations.

Example :

The inputs in the floating-point adder pipeline refer to two different normalized floating-point binary numbers. These are defined as follows:

$$ A = X * 2^x = 0.9504 * 10^3 $$

$$ B = Y * 2^y = 0.8200 * 10^2 $$

Where *x* and *y* refer to the exponents and *X* and *Y* refer to two fractions representing the mantissa.

The floating-point addition and subtraction process is broken into four pieces. The matching sub-operation to be executed in the specified pipeline is contained in each segment. The four segments depict the following sub-operations:

1. Comparing the exponents using subtraction

2. Aligning the mantissa

3. Adding or subtracting the mantissa

4. Normalizing the result

![Pasted image 20240613083407.png](/img/user/Images/Pasted%20image%2020240613083407.png)

The registers are placed after every sub-operation in order to store the intermediate results.

### 1. Comparing Exponents by Subtraction

The difference between the exponents is calculated by subtracting them. The result’s exponent is chosen to be the larger exponent.

The exponent difference, 3 – 2 = 1, defines the total number of times the mantissa associated with the lesser exponent should be shifted to the right.

### 2. Aligning the Mantissa

As per the difference of exponents calculated in segment one, the mantissa corresponding with the smaller exponent would be moved.

$$A = 0.9504 * 10^3$$

$$B = 0.08200 * 10^3$$


### 3. Adding the Mantissa

Both the mantissa would be added in the third segment.

$$C = A + B = 1.0324 * 10^3$$

### 4. Normalizing the Result

After the process of normalization, the result would be written as follows:

$$C = 0.1324 * 10^4$$
---
# Pipeline optimization techniques:

### 1. **Pipeline Depth and Stage Balancing**

- **Deep Pipelining**: Increasing the number of stages in a pipeline can enhance the clock speed, but it also increases the complexity and the potential for hazards.
- **Stage Balancing**: Ensuring that each pipeline stage takes roughly the same amount of time helps avoid bottlenecks and improves overall efficiency.

### 2. **Hazard Mitigation**

- **Data Hazards**: Techniques like forwarding (bypassing) and hazard detection units help mitigate issues when instructions depend on the results of previous ones.
- **Control Hazards**: Branch prediction and speculative execution are used to minimize the delay caused by control dependencies.
- **Structural Hazards**: Adding more resources (e.g., additional functional units) can help avoid conflicts when multiple instructions require the same hardware resources.
### 3. **Superscalar and Superpipelining**

- **Superscalar**: Multiple instructions are issued and executed per clock cycle by providing multiple execution units.
- **Superpipelining**: Increases the clock speed by reducing the time taken for each pipeline stage, effectively splitting stages into smaller sub-stages.

### 4. **Instruction Level Parallelism (ILP)**

- **Linked to Superscalar and Superpipelining**: Increasing the instruction throughput to reduce the overhead of loop control instructions.
- More on this below during module 3 section
### 5. **Compiler Techniques**

- **Instruction Scheduling**: Rearranging the order of instructions to avoid pipeline stalls.
- **Register Allocation**: Efficiently managing the use of registers to reduce memory access and pipeline stalls.

---

# Compiler Techniques for improving performance in the pipeline

Compiler techniques play a crucial role in optimizing the performance of the instruction pipeline in a CPU. These techniques focus on improving instruction scheduling, reducing hazards, and enhancing resource utilization.

Here are some compiler techniques for improving performance in the pipeline:

### 1. **Instruction Scheduling**

Instruction scheduling is a key optimization technique where the compiler rearranges the order of instructions to avoid pipeline stalls and maximize instruction throughput.

- **Static Scheduling**: The compiler analyzes the code at compile time and reorders instructions to minimize pipeline stalls. This is done by ensuring that data dependencies are respected while filling in delay slots caused by branches or other hazards.
- **Dynamic Scheduling**: In some cases, dynamic scheduling is employed at runtime by the hardware, but compilers can assist by providing hints or optimized sequences that can be dynamically adjusted.

### 2. **Loop Unrolling**

Loop unrolling is a technique where the compiler replicates the loop body multiple times, reducing the overhead of loop control instructions and increasing instruction-level parallelism.

- **Example**: Transforming a loop that iterates 100 times into a loop that iterates 25 times, with each iteration performing four times the original work.

### 3. **Software Pipelining**

Software pipelining involves reordering instructions from different iterations of a loop so that multiple iterations are overlapped, increasing parallelism and reducing idle time in the pipeline.

- **Example**: In a loop, the computation for the next iteration can begin before the current iteration finishes, effectively keeping all parts of the pipeline busy.

### 4. **Register Allocation**

Efficient register allocation minimizes the use of memory accesses, which are slower and can cause pipeline stalls.

- **Graph Coloring**: A common method where the compiler uses a graph to represent register interference and assigns registers in a way that minimizes conflicts.
- **Spilling**: When there are not enough registers, some variables are temporarily stored in memory. The compiler tries to minimize spilling by optimizing register usage.

### 5. **Dead Code Elimination**

Removing code that does not affect the program’s output can reduce the number of instructions and potential pipeline stalls.

- **Example**: Eliminating computations whose results are never used.

---
# Module 3

## Instruction level parallelism

Instruction level parallelism is a measure of how many of the operations in a computer program can be executed simultaneously.

## What is parallelism in terms of CPU?

![Pasted image 20240613090106.png](/img/user/Images/Pasted%20image%2020240613090106.png)

As the above diagram states, this processor with 4 sub processors can break down a program in 4 small parts and *execute these parts simultaneously*.

---
# The problem of Shared Dependency.

![Pasted image 20240613090250.png](/img/user/Images/Pasted%20image%2020240613090250.png)

Here the same processor can break down the program into three separate instructions and execute them simultaneously.

All three instructions are processed simultaneously in *1 unit time*.

Now take another set of instructions :

![Pasted image 20240613090527.png](/img/user/Images/Pasted%20image%2020240613090527.png)

Here as you can see in instruction 3, operand *u* is dependent on the values of the previous operands *s* and *t*.

So all three instructions cannot execute in unit time as instruction 3 needs to be put on hold for the values of the previous two operands, which introduces a stall in the processor.

Thus,

This phenomenon of stalling in a processor due to incomplete data is called *the problem of shared dependency*.

Now, to calculate the maximum level of parallelism that can be *exploited* in a program is a ratio called the *ILP ratio*.

It is calculated by *ILP* = *Total number of instructions* / *Total time taken to execute the instructions*

In the second program's case the *ILP* ratio is 3/2.

The *higher* the *ILP* ratio, *the better* it's *throughput is*.

Or we can say that *throughput* is ==inversely related== to *latency*.

---
## Architectural techniques to increase ILP

1. Superscalar architecture
2. VLIW
3. Superpipelining

## 1. Superscalar architecture

Let's see how a traditional instruction pipeline works:

![Pasted image 20240613092024.png](/img/user/Images/Pasted%20image%2020240613092024.png)

Here 

*IF* = Instruction Fetch
*ID* = Instruction Decode
*EX* = Execute
*MEM* = Memory
*WB* = Writeback

In this architecture only a single instruction gets executed in a single unit time.

Now, in case of a single instruction, *once fetching is done*, *IF stays idle till the current execution is complete*.
Once *Decoding is done*, *ID stays idle till the current execution is complete*.

And this goes on, decreasing productivity of the processor and the overall throughput is reduced.

Hence, enter, *Superscalar Architecture*

<?xml version="1.0" standalone="no"?><!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd"><svg width="978" height="571" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><rect x="0" y="0" width="100%" height="100%" fill="#ffffff" /><path fill="#98cb00" d="M437.5,10.5 L543.5,10.5 L543.5,560.5 L437.5,560.5 L437.5,10.5 z" /><path fill="#000000" id="legend" d="M13,139 L13,184 L10,184 L13.5,191 L17,184 L14,184 L14,139 L13,139 z M28.75,159 C 28.39102,159.00002 28.09161,159.12715 27.84375,159.375 C 27.59588,159.62288 27.46875,159.9223 27.46875,160.28125 C 27.46875,160.6317 27.59161,160.93538 27.84375,161.1875 C 28.09588,161.43965 28.39957,161.56252 28.75,161.5625 C 29.10042,161.56252 29.40411,161.43965 29.65625,161.1875 C 29.90838,160.93538 30.03124,160.63171 30.03125,160.28125 C 30.03124,159.92229 29.90411,159.62288 29.65625,159.375 C 29.40838,159.12715 29.10897,159.00002 28.75,159 z M28.90625,164.09375 L24.5,164.8125 L24.5,165.3125 C 25.08974,165.2185 25.46821,165.15626 25.65625,165.15625 C 25.88702,165.15626 26.05502,165.2241 26.1875,165.34375 C 26.31997,165.46341 26.40625,165.62448 26.40625,165.8125 C 26.40625,166.05183 26.2735,166.62234 26,167.5625 L24.3125,173.3125 C 24.09882,174.04755 24,174.59 24,174.90625 C 24,175.22249 24.12153,175.4781 24.34375,175.6875 C 24.56597,175.8969 24.83707,176 25.1875,176 C 25.71741,176 26.26255,175.7655 26.84375,175.3125 C 27.63007,174.70567 28.32505,173.9514 28.90625,173.0625 L28.46875,172.78125 C 27.97302,173.49066 27.48717,174.05288 27,174.4375 C 26.82051,174.57425 26.65945,174.62501 26.53125,174.625 C 26.42014,174.625 26.33119,174.58547 26.25,174.5 C 26.1688,174.41453 26.125,174.293 26.125,174.15625 C 26.125,174.03659 26.20406,173.66934 26.375,173.0625 L28.90625,164.09375 z M30.1875,216.90625 C 29.41826,218.16267 28.71768,219.05397 28.09375,219.5625 C 27.46982,220.07105 26.69017,220.46236 25.75,220.71875 L25.625,221.21875 L27.5625,221.21875 L25.40625,228.625 C 25.13274,229.57372 25,230.28847 25,230.75 C 25,231.11753 25.10443,231.42122 25.34375,231.65625 C 25.58306,231.89129 25.90518,232 26.28125,232 C 26.76843,232 27.24011,231.82479 27.71875,231.5 C 28.4196,231.02992 29.18242,230.23905 29.96875,229.09375 L29.53125,228.78125 C 28.82184,229.6616 28.36137,230.17281 28.15625,230.34375 C 27.80582,230.64289 27.52617,230.78124 27.3125,230.78125 C 27.21848,230.78125 27.13087,230.76442 27.0625,230.6875 C 26.99412,230.61058 26.96875,230.48905 26.96875,230.34375 C 26.96875,230.10443 27.10443,229.59322 27.34375,228.78125 L29.53125,221.21875 L31.53125,221.21875 L31.75,220.40625 L29.75,220.40625 L30.75,216.90625 L30.1875,216.90625 z M58,239 L58,242 L13,242 L13,243 L58,243 L58,246 L65,242.5 L58,239 z" /><path fill="#000000" d="M13,10 L13,121 L119,121 L119,231 L225,231 L225,341 L331,341 L331,451 L437,451 L437,561 L968,561 L968,450 L862,450 L862,340 L756,340 L756,230 L650,230 L650,120 L544,120 L544,10 L13,10 z M14,11 L119,11 L119,65 L14,65 L14,11 z M120,11 L225,11 L225,65 L120,65 L120,11 z M226,11 L331,11 L331,65 L226,65 L226,11 z M332,11 L437,11 L437,65 L332,65 L332,11 z M438,11 L543,11 L543,65 L438,65 L438,11 z M14,66 L119,66 L119,120 L14,120 L14,66 z M120,66 L225,66 L225,120 L120,120 L120,66 z M226,66 L331,66 L331,120 L226,120 L226,66 z M332,66 L437,66 L437,120 L332,120 L332,66 z M438,66 L543,66 L543,120 L438,120 L438,66 z M120,121 L225,121 L225,175 L120,175 L120,121 z M226,121 L331,121 L331,175 L226,175 L226,121 z M332,121 L437,121 L437,175 L332,175 L332,121 z M438,121 L543,121 L543,175 L438,175 L438,121 z M544,121 L649,121 L649,175 L544,175 L544,121 z M120,176 L225,176 L225,230 L120,230 L120,176 z M226,176 L331,176 L331,230 L226,230 L226,176 z M332,176 L437,176 L437,230 L332,230 L332,176 z M438,176 L543,176 L543,230 L438,230 L438,176 z M544,176 L649,176 L649,230 L544,230 L544,176 z M226,231 L331,231 L331,285 L226,285 L226,231 z M332,231 L437,231 L437,285 L332,285 L332,231 z M438,231 L543,231 L543,285 L438,285 L438,231 z M544,231 L649,231 L649,285 L544,285 L544,231 z M650,231 L755,231 L755,285 L650,285 L650,231 z M226,286 L331,286 L331,340 L226,340 L226,286 z M332,286 L437,286 L437,340 L332,340 L332,286 z M438,286 L543,286 L543,340 L438,340 L438,286 z M544,286 L649,286 L649,340 L544,340 L544,286 z M650,286 L755,286 L755,340 L650,340 L650,286 z M332,341 L437,341 L437,395 L332,395 L332,341 z M438,341 L543,341 L543,395 L438,395 L438,341 z M544,341 L649,341 L649,395 L544,395 L544,341 z M650,341 L755,341 L755,395 L650,395 L650,341 z M756,341 L861,341 L861,395 L756,395 L756,341 z M332,396 L437,396 L437,450 L332,450 L332,396 z M438,396 L543,396 L543,450 L438,450 L438,396 z M544,396 L649,396 L649,450 L544,450 L544,396 z M650,396 L755,396 L755,450 L650,450 L650,396 z M756,396 L861,396 L861,450 L756,450 L756,396 z M438,451 L543,451 L543,505 L438,505 L438,451 z M544,451 L649,451 L649,505 L544,505 L544,451 z M650,451 L755,451 L755,505 L650,505 L650,451 z M756,451 L861,451 L861,505 L756,505 L756,451 z M862,451 L967,451 L967,505 L862,505 L862,451 z M438,506 L543,506 L543,560 L438,560 L438,506 z M544,506 L649,506 L649,560 L544,560 L544,506 z M650,506 L755,506 L755,560 L650,560 L650,506 z M756,506 L861,506 L861,560 L756,560 L756,506 z M862,506 L967,506 L967,560 L862,560 L862,506 z" /><g id="t1"><path fill="#000000" id="pif" d="M52.374,51.499999 L52.374,24.499999 L55.947,24.499999 L55.947,51.499999 L52.374,51.499999 z M62.4115,51.499999 L62.4115,24.499999 L80.6264,24.499999 L80.6264,27.686219 L65.9845,27.686219 L65.9845,36.047749 L78.6557,36.047749 L78.6557,39.233969 L65.9845,39.233969 L65.9845,51.499999 L62.4115,51.499999 z" /><use x="0" y="55" xlink:href="#pif" /><path fill="#000000" id="pid" d="M156.413,51.499999 L156.413,24.499999 L159.986,24.499999 L159.986,51.499999 L156.413,51.499999 z M166.266,51.499999 L166.266,24.499999 L175.567,24.499999 C177.666,24.500029 179.269,24.628949 180.374,24.886769 C181.921,25.242859 183.241,25.887469 184.334,26.820599 C185.758,28.023899 186.823,29.561749 187.529,31.434169 C188.235,33.306629 188.588,35.446129 188.588,37.852659 C188.588,39.903149 188.348,41.720339 187.87,43.304229 C187.391,44.888139 186.777,46.198849 186.028,47.236359 C185.279,48.273879 184.459,49.090379 183.569,49.685879 C182.679,50.281379 181.605,50.732609 180.346,51.039559 C179.088,51.346519 177.642,51.499999 176.009,51.499999 L166.266,51.499999 z M169.839,48.313779 L175.604,48.313779 C177.384,48.313779 178.781,48.148029 179.794,47.816509 C180.807,47.484999 181.614,47.018419 182.216,46.416779 C183.063,45.569579 183.723,44.430769 184.195,43.000339 C184.668,41.569929 184.904,39.835619 184.904,37.797409 C184.904,34.973409 184.441,32.803219 183.514,31.286829 C182.587,29.770489 181.46,28.754459 180.134,28.238739 C179.177,27.870419 177.636,27.686239 175.512,27.686219 L169.839,27.686219 L169.839,48.313779 z" /><use x="0" y="55" xlink:href="#pid" /><path fill="#000000" id="pex" d="M254.935,51.499999 L254.935,24.499999 L274.458,24.499999 L274.458,27.686219 L258.508,27.686219 L258.508,35.955659 L273.445,35.955659 L273.445,39.123469 L258.508,39.123469 L258.508,48.313779 L275.084,48.313779 L275.084,51.499999 L254.935,51.499999 z M277.312,51.499999 L287.755,37.429059 L278.546,24.499999 L282.801,24.499999 L287.7,31.424969 C288.719,32.861549 289.443,33.966589 289.873,34.740109 C290.475,33.757859 291.187,32.732619 292.009,31.664389 L297.443,24.499999 L301.329,24.499999 L291.844,37.226469 L302.065,51.499999 L297.645,51.499999 L290.849,41.867669 C290.468,41.315149 290.076,40.713519 289.67,40.062759 C289.069,41.045029 288.639,41.720339 288.381,42.088679 L281.604,51.499999 L277.312,51.499999 z" /><use x="0" y="55" xlink:href="#pex" /><path fill="#000000" id="pmem" d="M343.291,51.499999 L343.291,24.499999 L348.669,24.499999 L355.06,43.617329 C355.649,45.397689 356.079,46.729879 356.349,47.613919 C356.656,46.631659 357.135,45.188959 357.786,43.285809 L364.25,24.499999 L369.057,24.499999 L369.057,51.499999 L365.613,51.499999 L365.613,28.901769 L357.767,51.499999 L354.544,51.499999 L346.735,28.515009 L346.735,51.499999 L343.291,51.499999 z M374.932,51.499999 L374.932,24.499999 L394.455,24.499999 L394.455,27.686219 L378.505,27.686219 L378.505,35.955659 L393.442,35.955659 L393.442,39.123469 L378.505,39.123469 L378.505,48.313779 L395.081,48.313779 L395.081,51.499999 L374.932,51.499999 z M399.943,51.499999 L399.943,24.499999 L405.321,24.499999 L411.712,43.617329 C412.301,45.397689 412.731,46.729879 413.001,47.613919 C413.308,46.631659 413.787,45.188959 414.438,43.285809 L420.902,24.499999 L425.709,24.499999 L425.709,51.499999 L422.265,51.499999 L422.265,28.901769 L414.419,51.499999 L411.196,51.499999 L403.387,28.515009 L403.387,51.499999 L399.943,51.499999 z" /><use x="0" y="55" xlink:href="#pmem" /><path fill="#000000" id="pwb" d="M468.528,51.499999 L461.364,24.499999 L465.029,24.499999 L469.136,42.199179 C469.578,44.053209 469.959,45.894959 470.278,47.724419 C470.965,44.839019 471.371,43.175319 471.493,42.733289 L476.632,24.499999 L480.942,24.499999 L484.809,38.165759 C485.779,41.554579 486.479,44.740799 486.909,47.724419 C487.253,46.017739 487.701,44.059349 488.253,41.849249 L492.489,24.499999 L496.081,24.499999 L488.677,51.499999 L485.233,51.499999 L479.542,30.927689 C479.063,29.208749 478.781,28.152819 478.695,27.759889 C478.412,29.000019 478.148,30.055959 477.903,30.927689 L472.175,51.499999 L468.528,51.499999 z M499.248,51.499999 L499.248,24.499999 L509.378,24.499999 C511.441,24.500029 513.095,24.773219 514.342,25.319579 C515.588,25.865989 516.564,26.707049 517.27,27.842769 C517.976,28.978539 518.329,30.166459 518.329,31.406549 C518.329,32.560729 518.016,33.647359 517.39,34.666439 C516.763,35.685549 515.818,36.508199 514.553,37.134379 C516.186,37.613249 517.442,38.429749 518.32,39.583899 C519.198,40.738069 519.637,42.100959 519.637,43.672579 C519.637,44.937249 519.37,46.112899 518.835,47.199519 C518.301,48.286159 517.641,49.124149 516.856,49.713509 C516.07,50.302869 515.084,50.747949 513.9,51.048769 C512.715,51.349589 511.263,51.499999 509.544,51.499999 L499.248,51.499999 z M502.821,35.845159 L508.66,35.845159 C510.244,35.845169 511.379,35.740809 512.067,35.532059 C512.976,35.261949 513.66,34.813799 514.121,34.187589 C514.581,33.561409 514.811,32.775599 514.811,31.830149 C514.811,30.933849 514.596,30.144969 514.167,29.463509 C513.737,28.782079 513.123,28.315509 512.325,28.063779 C511.527,27.812099 510.158,27.686239 508.218,27.686219 L502.821,27.686219 L502.821,35.845159 z M502.821,48.313779 L509.544,48.313779 C510.698,48.313779 511.508,48.270809 511.975,48.184859 C512.798,48.037519 513.485,47.791949 514.038,47.448159 C514.59,47.104369 515.045,46.604029 515.401,45.947129 C515.757,45.290249 515.935,44.532069 515.935,43.672579 C515.935,42.665769 515.677,41.790939 515.161,41.048089 C514.645,40.305259 513.93,39.783439 513.016,39.482609 C512.101,39.181799 510.784,39.031389 509.065,39.031379 L502.821,39.031379 L502.821,48.313779 z" /><use x="0" y="55" xlink:href="#pwb" /><path fill="#0000ff" d="M12 11 L12 121 L15 121 L15 11 L12 11 z" /></g><use x="106" y="110" xlink:href="#t1" /><use x="212" y="220" xlink:href="#t1" /><use x="318" y="330" xlink:href="#t1" /><use x="424" y="440" xlink:href="#t1" /></svg>

![Pasted image 20240613092630.png](/img/user/Images/Pasted%20image%2020240613092630.png)

==Basically what happens here that in the first instruction *As soon as* the fetching is done, the *fetching of the next instruction* starts, while the *first instruction is being decoded*.==

This architecture works on a *cascading domino style*  where *subsequent operations are triggered as soon as the resource for the previous operation is freed*.

Another easy to understand example diagram could be :

![Pasted image 20240613092916.png](/img/user/Images/Pasted%20image%2020240613092916.png)

![Pasted image 20240613110605.png](/img/user/Images/Pasted%20image%2020240613110605.png)

In each cycle, the dispatch unit retrieves and decodes up to two instructions from the front of the queue. If it is one integer, one floating point number and no hazards, then both the instructions are dispatched in the same clock cycle.

![Pasted image 20240613110813.png](/img/user/Discrete_Maths_Speedrun/Pasted%20image%2020240613110813.png)

--- 
# 2. VLIW architecture

VLIW stands for "Very long instruction Word"

![Pasted image 20240613110910.png](/img/user/Images/Pasted%20image%2020240613110910.png)

Contrary to the superscalar architecture, the VLIW architecture follows the principle of ==*putting a single large instruction in which involves a lot of different parts of a CPU* finishing *2-3 or more tasks in a single instruction cycle*==.

We could also view it as combining 2-3 or more tasks in a single instruction cycle.

However *it is not necessary* that a *CPU dealing with VLIW has only one of each component*(ALU, MU, CU).

An ideal CPU following VLIW has more than one components (each) to deal with large instructions.

![Pasted image 20240613111548.png](/img/user/Images/Pasted%20image%2020240613111548.png)

In the above digrammatical representation of the VLIW architecture, 

Instructions are stored in the *instruction cache* where according to each instruction, a final unit is assigned(ALU or MU)

*Operands are stored in the multi-ported register file* where they are fetched for instructions

The control unit manages the *overall functioning of the architecture*.

The functional units execute instructions and pass them to read/write cross bar *where it is decided what to do with the completed instructions*. 

---
# 3. Superpipelined architecture.

A superpipelined architecture in computer architecture is an advanced form of pipelining where *==instructions are divided into smaller tasks and executed concurrently in multiple stages==*. It improves the performance of a  standard pipeline by further reducing the execution time of instructions.

In a superpipelined architecture, each instruction goes through multiple stages such as 

Instruction fetch (*IF*), Instruction decode (*ID*), Execute (*EX*), memory access (*MEM*) and write-back (*WB*).

The next instruction *==can be loaded while the current instruction is being executed==* (*EX*), allowing for a seamless flow of instructions, like an assembly line.

![Pasted image 20240613112922.png](/img/user/Images/Pasted%20image%2020240613112922.png)

The diagram might look similar to superscalar, but the difference lies in the fact that in superscalar, *things happen one after another*, while in superpipelined architecture *things happen at the same time*, providing a huge difference in performance.



![WhatsApp Image 2024-05-14 at 13.13.56_6f4035e4.jpg](/img/user/Images/WhatsApp%20Image%202024-05-14%20at%2013.13.56_6f4035e4.jpg)
Diagram difference of superpipelined and superscalar architectures

---

# Difference between all the architectures.

![WhatsApp Image 2024-05-14 at 12.55.31_f9b63333.jpg](/img/user/Images/WhatsApp%20Image%202024-05-14%20at%2012.55.31_f9b63333.jpg)

*Ignore Out-of-Order-Execution.*

---
Array processor onwards are continued in module 4 pdf.






