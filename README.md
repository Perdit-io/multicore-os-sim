# Multicore OS Kernel Simulator

**A deterministic multi-core kernel simulator in C++20, architected to emulate mutex-based synchronization, demand paging, and virtual memory mechanics.**

![C++](https://img.shields.io/badge/Language-C++20-blue) ![License](https://img.shields.io/badge/License-MIT-green)

## Key Engineering Features

### 1. Thread-Safe Process Scheduling
Implemented a **deterministic discrete-event simulation** of multicore processing.
* **Synchronization:** Enforces thread safety using `std::mutex` to prevent race conditions during process context switching.
* **Scheduling Algorithms:** Configurable **Round Robin (RR)** and **First-Come-First-Serve (FCFS)** logic to analyze turnaround times and CPU utilization.

### 2. Virtual Memory Management (MMU)
Engineered a simplified **Memory Management Unit** to handle resource constraints.
* **Demand Paging:** Implements lazy allocation, fetching pages from a backing store only when a Page Fault occurs.
* **Memory Protection:** Enforces strict process isolation; unauthorized memory access triggers immediate termination.

### 3. Interactive Shell (CLI)
Built a custom shell to manage the OS state dynamically, inspired by tools like `screen` and `nvidia-smi`.

---

## System Commands

The simulator exposes a shell interface for system administration:

| Command | Description |
| :--- | :--- |
| `process-smi` | **System Management:** Displays memory usage and CPU core allocation. |
| `vmstat` | **Virtual Memory:** Detailed stats on active/inactive pages and paging rates. |
| `screen -s <name>` | Spawns a process with defined memory requirements. |
| `screen -r <name>` | Context switches the terminal to a running process. |
| `scheduler-start` | Triggers the CPU scheduling algorithm. |
| `help` | Displays full command list. |

---

## Build & Run

### Prerequisites
* C++20 Compatible Compiler (GCC 10+ or Clang)

### Compilation

**Windows (PowerShell):**
```powershell
g++ -std=c++20 -Wall -Wextra -Werror Main.cpp Kernel.cpp ShellPrompt.cpp Process.cpp Processinstruction.cpp -o csopesy.exe

```

**macOS / Linux (Bash):**

```bash
g++ -std=c++20 -Wall -Wextra -Werror Main.cpp Kernel.cpp ShellPrompt.cpp Process.cpp Processinstruction.cpp -o csopesy

```

### Usage

1. **Configure:** Edit `config.txt` in the root directory to set RAM size, Time Quantum, and Core count.
2. **Run:**
```bash
./csopesy

```

---

## Credits

* **Angeles, Marc Andrei D.:** Lead Architect (Core Kernel Rewrite, Scheduler, Memory Paging).
* **Limbag, Daniella Franxene P.:** Initial Prototype & Base Implementation.
* **Gomez, Dominic Joel M. & Iral II, John Rovere N.:** Reporting Modules & Documentation.
