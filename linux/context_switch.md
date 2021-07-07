## Concepts

Thread state: *private* states such as program counter, registers, and execution
stack; *shared* states including global variables, heap, and file system.

TCB (thread control block): has states of threads not running; 1 per thread;
contains execution state and scheduling info.

## Software Side

A context switch can be triggered either by a system call or by a timed interrupt.
The switch to kernel mode saves the user space thread's registers.

## Hardware Side


## Linux Implementation

