# RISC-V-processor
### Why RISC-V Processors?

Any complex electronic system is composed of hardware and software.
We create hardware using complex SOC. So this SOC will have almost all the components needed for the system. And the processor is going to be the main component.
So whatever the application we run, all applications will be converted into processor instructions and eventually all the instructions will be executed by the processor.
The SOC can have a dual or quadcore processor to run multiple applications in parallel and that's what the operating system does.
For example-- when we click on any particular mobile application, the operating system loads the equivalent binary into RAM and then it loads the starting address of the binary into the program counter. All the processor has a special register called program counter and the program counter will increment sequentially and that is how the processor is going to fetch all the instructions from the memory.
So this particular application which we click on, has already been compiled into the processor instructions in terms of binary i.e. machine language and that is stored in storage memory.

Coming to the software, there could be many layers-- `application software` (created using a high-level language like C, C++, Java), `operating system` (manages i/o operations, and memory and is responsible for running many applications in parallel), `RISC-V compiler`, `RISC-V Assembler`.

![image](https://github.com/Pisinha26/VSDSquadron-Mini-Research-Internship/assets/140955475/a1a03093-3cbe-434b-8e55-8bc4e718da86)


![image](https://github.com/Pisinha26/VSDSquadron-Mini-Research-Internship/assets/140955475/bf18c839-dba9-4754-914f-849d1ae0a753)


![WhatsApp Image 2024-04-26 at 23 09 37](https://github.com/Pisinha26/VSDSquadron-Mini-Research-Internship/assets/140955475/b8cec056-82c4-4d54-88a1-a4f0b0a2fbf2)


To convert the assembly language program into a machine language program, it follows RISC-V ISA which defines the format of the instructions like `R-type`, `I-type`, `S-type`, `B-type`, `U-type`, and `J-type`. So based on the format, the instructions get converted into binary.


## C-code Compilation Process

![Screenshot 2024-04-26 233426](https://github.com/Pisinha26/VSDSquadron-Mini-Research-Internship/assets/140955475/3f9def57-ce31-4d0d-b072-7164ebdfee82)


## RISC-V ISA & Processor

![WhatsApp Image 2024-04-26 at 23 09 36](https://github.com/Pisinha26/VSDSquadron-Mini-Research-Internship/assets/140955475/b9b1c971-cc44-4563-a559-a49a11d4ce9f)

It's an abstract interface between low-level software (compiler, Assembler) and low-level  hardware(processor). 
An embedded system engineer is going to refer to RISC-V ISA and based on the specifications he is going to design the compiler.
So basically the compiler should support all the instructions and be able to convert any kind of high-level language into RISC-V  assembly language.
VLSI engineer is also going to look at RISC-V ISA as a golden reference and he will implement the RTL design.


## RISC-V Execution Stages

![WhatsApp Image 2024-04-26 at 23 09 35](https://github.com/Pisinha26/VSDSquadron-Mini-Research-Internship/assets/140955475/9cf57d4d-6e2c-4d35-981b-e00d54dcb50b)


The RISC-V processor works through 5 stages--
`Fetch`,  `decode`,  `execute`,  `memory`,  `write back`.
* <b>Fetch</b>-- The instructions will be loaded in instruction memory, so the processor is going to read the instructions mostly sequentially and sometimes in a non-sequential manner. the processor has got a special register called program counter which will always increment by 4 because in RISC-V we do byte addressing. This is how the processor will fetch the instructions from memory.
* <b>Decode</b>-- Then the decoder will decode the instructions.
* <b>Execute</b>-- The decoder will then communicate to the ALU what kind of operations it has to perform. So as part of the execution, the ALU is going to perform operations like arithmetic operations, logic operations, shift operations, etc. and based on the functionality, it is going to produce the output, and the results will be stored sometimes in memory and most of the time, it will be stored back  into the registers. 
* <b>Memory</b>-- the values will be written in the memory or sometimes read the values from the memory.
* <b>Write back</b>-- Most of the time whatever the results ALU produces will be written back to the register primarily in the destination registers.


### RISC-V Instruction Set Architecture


![WhatsApp Image 2024-04-27 at 00 10 12](https://github.com/Pisinha26/VSDSquadron-Mini-Research-Internship/assets/140955475/443fd00a-1e49-479f-9c3e-16e7f3ca7ec0)

Overall the performance depends on various parameters.
* `Algorithm` decides how many instructions could be there and based on the algorithm we choose to implement a particular software application which decides how many instructions it is going to demand.
* Also, the choice of a `Programming language` defines no of instructions per program. i.e. there is a difference between C and C++. C++ might demand less no of instructions because it is more based on object-oriented programming.
* The performance also depends on how we design the `compiler`. If the compiler is efficient enough to produce fewer instructions, then it will have a huge impact on the instruction count.
* `ISA` which is the definition for both the  compiler and processor design, controls everything such as instructions count, CPI, and clock rate. 
When it comes to hardware, we look at how to improve the performance of the hardware by reducing the clock period(seconds/clock cycle), then we would be able to improve the frequency and then we can execute more no of instructions.


![WhatsApp Image 2024-04-27 at 00 39 37](https://github.com/Pisinha26/VSDSquadron-Mini-Research-Internship/assets/140955475/8e7283b0-04f3-401c-bb6c-989b6e8b2638)


This is how we can visualize the ISA. It defines the main components like `registers file`, `ALU`, and `Memory`. So the memory is going to have both-- Instruction(machine language) and data(binary). Everything is going to be 32 bits i.e. whatever the assembly program we write, is going to be converted into 32 bits which is machine language and that is stored in the memory. In memory, we do byte addressing and also there is a register file that contains 32 registers each of 32 bits. So RV32I means RISC-V 32-bit integer instructions. The ALU sometimes writes the results into registers and sometimes it writes into memory. So we need different kinds of instructions {R (register type) and I (immediate type)} to support data flow between registers and ALU. To implement data flow between registers and memory we need additional instructions like `I` and `S` type instructions. We also need other types of instructions for control flow which are `B`, `J`, `U`, and `I` type instructions.


<b>RISC-V RV32I Instruction Set</b>
* `R-type` : Register to Register instructions
* `I-type` : Register Immediate, Load, JLR, Ecall & Ebreak
* `S-type` : Store
* `B-type` : Branch
* `J-type` : Jump & Link
* `U-type` : Load/Add upper Immediate
