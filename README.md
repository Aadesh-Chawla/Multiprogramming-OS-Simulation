# Multiprogramming Operating System (MOS) Project

The **Multiprogramming Operating System (MOS)** project simulates a simple operating system capable of managing multiple programs in a controlled environment. This project is divided into two phases, each introducing crucial OS functionalities, from basic program handling to advanced memory management, paging, and interrupt handling. The goal of this project is to explore core concepts of operating systems, including memory management, job control, and efficient handling of program errors.

---

## Table of Contents
- [Project Overview](#project-overview)
- [Phase 1 Overview](#phase-1-overview)
- [Phase 2 Overview](#phase-2-overview)
- [Setup and Execution](#setup-and-execution)
- [Future Enhancements](#future-enhancements)

---

## Project Overview

This project is a multi-phase implementation of a **Multiprogramming Operating System** (MOS) that manages various jobs sequentially. Each job is loaded, executed, and monitored for errors in a simulated environment. The MOS follows a simplistic yet effective approach to understanding job processing, error handling, and memory allocation without using physical hardware.

The MOS project serves as an educational tool to grasp fundamental OS concepts:
- **Job Loading and Execution**: Simulating how a program is loaded and executed.
- **Error Handling**: Managing different types of errors in program execution.
- **Memory Management**: Using basic paging techniques to allocate and manage memory.
- **Interrupts**: Implementing different interrupts for program control.

The project repository is organized into phases:
- **Phase 1**: Basic job loading, instruction execution, and fundamental error handling.
- **Phase 2**: Enhanced memory management using paging, along with detailed error management and interrupt handling.

---

## Phase 1 Overview

The first phase of MOS introduces the basic architecture for loading, executing, and managing programs. Key aspects of this phase include:
- **Job Loading**: Jobs are loaded into memory using control cards.
- **Execution Flow**: A simple control loop for executing jobs, handling input and output.
- **Error Management**: Basic error types are recognized, ensuring each job is handled properly in case of execution errors.
- **Registers and Counters**: Minimal registers are used to simulate program control, along with counters to monitor runtime conditions.

The objective of Phase 1 is to simulate a multiprogramming environment, focusing on single job execution and understanding how basic job control and error handling operate within an OS.

---

## Phase 2 Overview

Building on Phase 1, the second phase of MOS introduces advanced features to improve job processing, memory management, and error handling. Key functionalities added in Phase 2 include:
- **Paging**: Implements a paging mechanism, which organizes memory into pages and enables dynamic allocation for each job.
- **Interrupts**: Introduces program, service, and timer interrupts to handle various program errors and runtime limits.
- **Process Control Block (PCB)**: Manages each job’s state and provides structured job control.
- **Detailed Error Handling**: A refined error management system with termination messages and unique error codes for various program errors.
- **Registers and Components**: Enhanced usage of registers and memory, with page tables and a Page Table Register (PTR) to manage memory mapping.

Phase 2 emphasizes the importance of memory isolation, error handling through interrupts, and efficient memory mapping, representing a closer approach to real OS memory management.

