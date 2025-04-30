#  Hybrid Parallel Sudoku Solver (OpenMP + MPI)

This project implements a **hybrid parallel Sudoku solver** designed to solve large puzzles (e.g., 16×16, 25×25) efficiently using both **OpenMP** (shared memory) and **MPI** (distributed memory). It supports multiple parallelization strategies including dynamic scheduling to overcome load imbalance across threads and processes.

The solver uses a backtracking-based algorithm and includes:
- A serial version (baseline)
- An OpenMP-only version (multithreaded single node)
- A hybrid MPI + OpenMP version (static and dynamic scheduling)
- Bootstrapper and task queue components to enable parallelism

---

##  Installation

###  Prerequisites
Ensure the following are installed on your system:
- C++ compiler with OpenMP support (e.g., `g++`, `clang++`)
- MPI implementation (e.g., OpenMPI or MPICH)
- `make` (optional but recommended)


##  Usage Instructions

###  Folder Structure

- `test_cases/` — contains example Sudoku puzzle files  
- `solutions.txt` — file where solutions are written  
- `run` — compiled executable for all modes


###  Command Formats

#### 1. Serial Mode

./run 16 test_cases/test16_1min.sdk solutions.txt 0  (16x16)

./run 25 test_cases/test25_5min.sdk solutions.txt 0  (25x25)

#### 2. OpenMP Mode (Multithreaded)

./run 16 test_cases/test16_1min.sdk solutions.txt 1 512  (16x16)

./run 25 test_cases/test25_5min.sdk solutions.txt 1 512  (25x25)

#### 3. MPI + OpenMP (Static Scheduling)

mpirun -np 4 ./run 16 test_cases/test16_1min.sdk solutions.txt 2 512 512 0 0  (16x16)

mpirun -np 4 ./run 25 test_cases/test25_5min.sdk solutions.txt 2 512 512 0 0  (25x25)

#### 4. MPI + OpenMP (Dynamic Scheduling)

mpirun -np 4 ./run 16 test_cases/test16_1min.sdk solutions.txt 3 512 512 1 123  (16x16)

mpirun -np 4 ./run 25 test_cases/test25_5min.sdk solutions.txt 3 512 512 1 123  (25x25)

## Test Cases
Test puzzles are located in the test_cases/ folder and include the following:

### 16×16 Sudoku Puzzles
test16_1min.sdk — Test 1 (easiest)

test16_5min.sdk — Test 2 (medium)

test16_15min.sdk — Test 3 (hard)

### 25×25 Sudoku Puzzles
test25_5min.sdk — Test 1 (easiest)

test25_15min.sdk — Test 2 (medium)

test25_28min.sdk — Test 3 (hardest)

These test cases were manually modified to reflect increasing difficulty and used to evaluate performance across different solver configurations.

## Team Members
Chirag Hegde

Email: chegde@ncsu.edu
