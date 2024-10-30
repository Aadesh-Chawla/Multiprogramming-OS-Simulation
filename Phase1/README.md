# Multiprogramming OS Job Execution Simulation

## Project Overview
This project simulates the basic operations of a multiprogramming operating system, focusing on executing jobs in memory. It demonstrates core OS functionalities such as job scheduling, memory management, and instruction execution. By interpreting simple commands from an input file, the system mimics how an OS manages job processing, executes instructions, and performs basic input/output operations.

## Features Demonstrated
From an operating system perspective, this project illustrates:

- **Multiprogramming**: Simultaneously handling multiple jobs by sequentially loading and executing them in memory.
- **Job Scheduling**: Simulating a simplistic job scheduling mechanism where each job is executed sequentially.
- **Memory Management**: Storing job instructions in a predefined memory array, loading and reading data as needed.
- **Basic Instruction Set Execution**: Processing a set of instructions (`GD`, `PD`, `LR`, `SR`, `CR`, `BT`, `H`) similar to machine instructions.
- **System Calls for I/O Operations**: Handling system calls for reading and writing data to simulate I/O operations in a controlled manner.

## Code Structure
The code consists of the following main components:

### 1. Classes and Variables
- **VM (Virtual Machine)**: The main class that simulates the job execution environment.
- **Memory**: A 100x4 array representing a limited memory capacity for storing job instructions.
- **IR (Instruction Register)**: Holds the current instruction.
- **R (General Purpose Register)**: Used for temporary data storage.
- **IC (Instruction Counter)**: Tracks the memory location of the current instruction.
- **SI (System Interrupt)**: Determines the type of system call to execute.

### 2. Functions
- `init()`: Initializes memory, registers, and other variables.
- `MOS()`: The Master Operating System function handles system interrupts for `READ`, `WRITE`, and `TERMINATE` commands.
- `LOAD()`: Loads job instructions and data into memory, identifying special markers (`$AMJ`, `$DTA`, `$END`) to start new jobs, load data, and mark the end of a job.
- `STARTEXE()`: Starts executing a job after it has been loaded into memory.
- `EXECUTEUSERPROGRAM()`: Iterates over memory, interpreting and executing instructions.
- `READ()`: Reads data from the input file into memory based on the instruction pointer.
- `WRITE()`: Writes memory data to an output file.
- `TERMINATE()`: Ends the job and prepares for the next one.

### 3. Instruction Set
The code simulates a set of simplified machine instructions:

- **GD (Get Data)**: Loads data into memory from the input file.
- **PD (Put Data)**: Outputs data from memory to the output file.
- **H (Halt)**: Terminates the current job.
- **LR (Load Register)**: Loads data from memory to register `R`.
- **SR (Store Register)**: Stores data from register `R` to memory.
- **CR (Compare Register)**: Compares `R` with a memory location, setting the toggle `C` to true if equal.
- **BT (Branch if True)**: Jumps to a specific memory address if `C` is true.

## Execution Flow
1. **Job Loading**: Reads the input file line-by-line to load job instructions into memory.
2. **Instruction Execution**: Begins executing instructions sequentially from memory, interpreting and executing each command.
3. **System Interrupts**: Uses `MOS()` to handle system calls (`READ`, `WRITE`, and `HALT`).
4. **Job Termination**: After completing a job, the system resets and prepares for the next job.

## Input/Output Example

### Input File Format
The input file (`input_Phase1.txt`) should contain job instructions and data.

- `$AMJ`: Start of a new job.
- `$DTA`: Data loading section, marking the start of data input for the job.
- `$END`: Marks the end of the job.
  
Program instructions such as `GD`, `PD`, `H`, etc., should follow this format.

### Output File
The program writes job results to `output_1.txt`.
