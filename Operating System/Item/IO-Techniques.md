# I/O Techniques
- Programmed I/O
  > http://inputoutput5822.weebly.com/programmed-io.html
  ## Overview
  **Processor execute a program to direct control**  
  **Need to wait for I/O module to respond**  
  **I/O module must interpret the address lines**
  ![Programmed I/O](Image/programmed_io.png)
  
  | Advantage | Disadvantage |
  | --- | --- |
  | Simple to implement | Low utilization of CPU |
  ## Command
  - Control: activate a peripheral and tell it what to do
  - Test: Test status conditions (power on-off, completed and errors)
  - Read: I/O module to obtain data from the peripheral and place it in an internal buffer  
          I/O module place it on the data bus when processor request obtaining data
  - Write: I/O module takes data from the data bus and transmits it to the peripheral
  ## Instruction
  | Isolated I/O | Memory Mapped I/O |
  | --- | --- |
  | Separate memory space | Memory from the main memory |
  | Limited instructions can be used <br/> IN, OUT, INS, OUTS | Any instruction which references to memory |
- Interrupt-driven I/O
  > http://inputoutput5822.weebly.com/interrupt-driven-io.html
  ## Overview
  **Similar to programmed I/O**  
  **Can execute other program while waiting I/O module to respond**  
  ![Interrupt Driven I/O](Image/interrupt_driven_io.png)
  
  | Advantage | Disadvantage |
  | --- | --- |
  | Fast than programmed I/O | Tricky to write if using a low-level language |
  | High utilization of CPU | Usually done by the hardware manufacturer |
  ## Instruction
  **To determine an interrupt signal in multiple I/O modules with the processor**  
  **To process multiple interrupts with the processor**
  
  ---
  
  ### Solving
  - Multiple Interrupt Lines (high priority)  
    **Provide multiple interrupt lines between processor and I/O modules**
    **Not practical**
  - Software Poll (ordered priority)  
    **Interrupt branches to an interrupt service routine**  
    **Every I/O module has an addressable status register and can be read by the processor to determine the interrupting module**  
    **Poll with the command line and place on the address line**
    **Time consuming**
  - Daisy Chain (Hardware Poll, Vectored, ordered priority)  
    **Processor propagate interrupt acknowledgment throughout the series of I/O modules until requesting module**  
    **Module responds by placing a word (vector - address or specific identifier) on the data lines**  
    **Processor directs the module based on vector**  
    **Removes the need for interrupt-service routine**
  - Bus Arbitration (Vectored, high priority)  
    **I/O module gaining control over the bus before requesting for the interrupt**  
    **Processor sends interrupt acknowledgment then requesting module places vector on the data lines**  
    Limited to only one module at a time
- Direct memory access (DMA)
  > http://inputoutput5822.weebly.com/direct-memory-access.html  
  > https://en.wikipedia.org/wiki/Direct_memory_access#Burst_mode
  ## Overview
  **Transfer data between main memory and external device without passing through the processor**  
  **Processor has to share system bus with DMA module**  
  **Only consume time when data transfer**  
  **More efficient when large volume of data has to be transferred**  
  ![Direct memory access](Image/direct_memory_access.png)
  
  | Advantage | Disadvantage |
  | --- | --- |
  | Read / write memory not through processor | Increases system cost (DMA controller) |
  | Faster processing | Need to solve cache coherence problems |
  ## Instruction
  ### Mode
  - Burst mode  
  **Transfer block of data in one contiguous sequence**  
  **Transfers all data in the data block before releasing control of system buses back to the CPU**  
  **CPU long periods of time inactive**
  - Cycle stealing mode  
  **System bus requested via BR and deasserted via BG to CPU (one byte)**  
  **Slower than burst mode**  
  **CPU idle is not longer than burst mode**  
  **Useful for monitor data in real time.**
  - Transparent mode  
  **Only transfers data when CPU does not use system buses**  
  **Needs to determine CPU is not using the system buses (complex)**  
  **CPU never stops executing its programs**  
  **DMA transfer is free in terms of time**  
  **Takes the most time to transfer a block of data**  
  **Most efficient in terms of overall system performance**
  ### Cache conherence
  - Bus snooping  
  **External writes are signaled to the cache controller**  
  **Cache invalidation for DMA writes**  
  **Cache flush for DMA reads**
  - Managed by software  
  **Flush cache line before outgoing DMA transfer**  
  **Invalidated cache line before DMA transfer access memory range (not accessed by any running threads)**  
  **Introduces some overhead to the DMA operation (loop to invalidate each cache line)**
  - Hybrids  
  **L2 cache is coherent**  
  **L1 cache (typically on-CPU) is managed by software**
  ### Configurations
  - Single-bus, detached DMA  
  **Share the same system bus**  
  **DMA module (surrogate processor) uses programmed I/O to exchange data between memory and an I/O module**  
  **Transfer a word consumes two bus cycles (inefficient)**  
  **Inexpensive**  
  ![Single-bus, detached DMA](Image/detached_dma.png)
  - Single-bus, integrated DMA  
  **DMA module:**  
    **Controls multiple I/O modules (not include system bus)**  
    **Only to exchange data with memory using system bus that shares with the processor**  
    **Exchange data outside system bus with I/O modules**  
  ![Single-bus, integrated DMA](Image/integrated_dma.png)
  - I/O bus  
  **I/O modules are connected to the DMA module using an I/O bus (reduce I/O interfaces)**  
  **Easily expandable configuration**  
  **Only to exchange data with memory using system bus that shares with the processor**  
  **Exchange data outside system bus with I/O modules**  
  ![I/O bus](Image/io_bus_dma.png)
