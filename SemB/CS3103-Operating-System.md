<kbd># Hardware
## Main Memory(RAM)
- A set of locations(sequentially numbered addresses) stores data and programs
- Volatile (lost  when computer shut down)
## I/O Modules
- Moves data between the computer and the external environment
## System Bus
- communication among processors, main memory, and I/O modules
## Program Counter(PC)
– holds address of the next instruction to be fetched
## Instruction Register(IR)
– store fetched instruction
## Accumulator(AC)
– store execution result temporarily</kbd>

<kbd># Processor
**Control Unit and Arithmetic & Logic Unit(ALU)**  
![Machine Cycle](../Image/machine_cycle.png)
## Type
### Microprocessor
– Contains a processor on a single chip
### Multiprocessors
– Contains multiple processors(cores) on a single chip
### Graphical Processing Units(GPUs)
- Single-Instruction Multiple Data(SIMD) techniques 
- efficient computation on arrays of data
### Digital Signal Processors(DSPs) 
- Encoding/decoding speech and video (codecs)
- Provide support for encryption and security
### System on a Chip (Soc)
- handheld devices
- CPUs, caches, DSPs, GPUs, I/O devices and main memory(same chip)</kbd>

<kbd># Instruction Execution
**Fetches => Decodes => Executes => Stores**
1. Instruction fetch (IF => fetch)
  a. Fetch main memory address that stores in PC
  b. Store instruction to IR
  c. PC point to next instruction address
2. Instruction decode and register fetch (ID => decode)
  - Interpret current instruction – opcode and operand(address)
3. Execute (EX => execute)
  a. Store operand in memory address register(MAR)
  b. Fetch data with MAR address and store in memory data register(MDR)
  c. Simple data – Pass to AC
4. Register write back (WB => store)</kbd>

<kbd># Program Status Word(PSW)
**Contains execution status information**
## Conditional Flags
### Carry(CY)
### Parity(P)
### Auxiliary carry(AC)
### Zero(Z)
### Sign Flag(S)
### Overflow flag(OV)
## Control Flags
### Trap
### Interrupt
### Direction</kbd>
