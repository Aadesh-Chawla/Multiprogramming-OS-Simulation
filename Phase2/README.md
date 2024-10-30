# Multiprogramming Operating System (MOS) - Phase 2

This project is the second phase of the Multiprogramming Operating System (MOS), introducing key functionalities like error handling, paging, and process control. This README provides a detailed guide on setting up, using, and understanding the MOS, specifically in Phase 2.

---

## Table of Contents
1. [Introduction](#introduction)
2. [System Overview](#system-overview)
3. [Paging Mechanism](#paging-mechanism)
4. [Interrupt Handling](#interrupt-handling)
5. [Components and Registers](#components-and-registers)
6. [Execution Flow](#execution-flow)
7. [Error Messages and Termination Codes](#error-messages-and-termination-codes)
8. [Setup and Execution](#setup-and-execution)

---

## 1. Introduction
The MOS Phase 2 project is designed to simulate a multiprogramming environment, handling job processing, memory management via paging, and managing program errors. This phase builds on Phase 1 with these enhancements:
- Program errors managed through Program Interrupts (PI).
- Time limit errors handled by Timer Interrupts (TI).
- A paging system for memory allocation.
- Enhanced job control with Process Control Blocks (PCB).
- Detailed error messages for easier debugging.

---

## 2. System Overview
The MOS provides a controlled environment to execute programs, where each job may encounter various errors, all managed effectively. The key upgrades in Phase 2 include:
- **Paging**: Organizes memory into pages for efficient allocation.
- **Interrupts**: Controls various error-handling operations.
- **Error Management**: Detailed error codes and termination messages.
- **Execution Control**: Only one job is executed at a time, with PCBs managing job control.

---

## 3. Paging Mechanism
Paging is a significant feature in Phase 2, allowing better memory management and job isolation:
- **Page Table**: Each job has a page table stored in real memory, mapping Virtual Addresses (VA) to Real Addresses (RA).
- **Page Allocation**: Pages are allocated to one of 30 memory blocks, with randomized allocation to avoid memory fragmentation.
- **Address Mapping**: Virtual addresses are translated to real addresses using the page table. Errors, such as page faults, are handled via the `ADDRESS MAP` routine.
- **PTR (Page Table Register)**: Stores the page table address for each job, enabling fast memory access.

This system ensures that each job's memory requirements are managed without conflicts, maintaining data integrity across jobs.

---

## 4. Interrupt Handling
Interrupts are essential to ensure smooth and controlled program execution. Phase 2 introduces:
- **Service Interrupt (SI)**: Handles input (GD), output (PD), and program termination (H).
- **Program Interrupt (PI)**: Triggered for various program errors:
  - PI=1: Operation error.
  - PI=2: Operand error.
  - PI=3: Page fault (attempts to load the correct page if valid).
- **Timer Interrupt (TI)**: Indicates if a job has exceeded its allotted time (TI=2), terminating if necessary.

Interrupt handling helps maintain system stability by ensuring jobs are corrected or terminated as needed.

---

## 5. Components and Registers
MOS Phase 2 utilizes the following components and registers:

- **Memory (M)**: Stores all jobs, data, and page tables.
- **Registers**:
  - **IR (Instruction Register)**: Holds the current instruction.
  - **IC (Instruction Counter)**: Points to the next instruction.
  - **R (General Purpose Register)**: Temporary storage for instruction execution.
  - **PTR (Page Table Register)**: Points to the page table for each job.
  - **C (Toggle Register)**: Stores the comparison flag.
- **PCB (Process Control Block)**: Maintains the state, limits, and counters for each job.
- **Counters**:
  - **TTC (Total Time Counter)**: Tracks total execution time.
  - **LLC (Line Limit Counter)**: Tracks lines written by a job.
  - **TTL (Total Time Limit)** and **TLL (Total Line Limit)**: Define the maximum allowed time and lines for each job.

---

## 6. Execution Flow
MOS follows a looped execution flow, moving through loading, executing, handling errors, or job completion:
1. **Initialization**: SI and TI are set up for service requests and time-based interrupts.
2. **Load Phase**:
   - Control cards `$AMJ` and `$DTA` mark the start and end of job data.
   - Program pages load into allocated frames, updating the page table.
3. **Execution Phase**:
   - `STARTEXECUTION` begins at `IC = 0`.
   - `EXECUTEUSERPROGRAM` runs, executing instructions sequentially.
4. **Interrupts**: Upon any interrupt (PI, SI, or TI), the system enters master mode for handling.
5. **Termination**: Jobs terminate with error messages as needed (see Error Messages and Termination Codes below).

---

## 7. Error Messages and Termination Codes
MOS Phase 2 uses specific error messages for job termination. Codes include:
- **Out of Data (EM=1)**
- **Line Limit Exceeded (EM=2)**
- **Time Limit Exceeded (EM=3)**
- **Operation Code Error (EM=4)**
- **Operand Error (EM=5)**
- **Invalid Page Fault (EM=6)**

Each termination includes a message in the output file, separated by two blank lines for readability.
