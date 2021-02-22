# Operating System

## Overview
- Controls the execution of application programs
- An Interface between applications and hardware
- Making a computer more convenient to use (Convenience)
- Allowing computer resources to be used efficiently (Efficiency)
- Permitting effective development, testing and introduction of new system functions without interfering with service (new / upgrade hardware, new services, fixes)  
![OS interface](Image/os_interface.png)

## Service
- Program development (editor and debugger)
- Program execution
- Access I/O devices (read and write)
- Controlled access to files (protection and permission)
- System access (user authorization)
- Error detection and response (deal with error)
- Accounting (collect usage statistics and monitor performance)

## Instruction Execution
1. Instruction fetch (IF - Fetch)  
  a. Fetch main memory address that stores in PC  
  b. Store instruction to IR  
  c. PC point to next instruction address
2. Instruction decode and register fetch (ID - Decode)  
**Interpret current instruction – opcode and operand(address)**
3. Execute (EX - Execute)  
  a. Store operand in memory address register(MAR)  
  b. Fetch data with MAR address and store in memory data register(MDR)  
  c. Simple data – Pass to AC
4. Register write back (WB - Store)

## Interrupt
**Typically indicate that some device or software needs service**
### Type
- Hardware Interrupt (External)
- Internal Interrupt (Error while executing)
- Software Interrupt
### Flow
![Memory Stack](Image/memory_stack.png)  
1. Use interrupt line to signal the processor  
2. Wait processor finishing the current instruction  
  **Need to wait till completion of important jobs (atomic operation)**  
3. Processor send signal acknowledgement of interrupt  
4. Push PSW, PC and other registers(if needed) onto control stack  
5. Use interrupt ID to find the Interrupt Service Routine(ISR) address in interrupt vector  
6. Load new PC value based on interrupt  
7. Check the interrupt finish or not (if needed)  
8. Restore the all value and continue executing instruction
> https://www.geeksforgeeks.org/difference-between-hardware-interrupt-and-software-interrupt/

| Type | Hardware | Software |
| :---: | --- | --- |
| Generation | External device or hardware | Any internal system |
| PC | No increment | Increment |
| Method | invoked with external device | Invoked INT instruction |
| Priority | Lowest than software interrupts | Highest |
| Synchronous | Asynchronous | Synchronous |
| Type | Maskable Interrupt <br/> Non Maskable Interrupt | Normal Interrupts <br/> Exception |
| Example | Keystroke depressions and mouse movements | All system calls |
