## Background

- ASLR is implemented to reduce the attack surface.
- ASLR randomizes the virtual memory layout either every time a new execution starts
or on system reboot.

## Problems


## Insights

2 Key operations: set the system in a specific state >> measure the duration of a certain
memory access. Perform them for every probed address.

We only need 1 measurement without interruption.

## Attack Model

- Assume an adversary who has restricted access to the system but does not have access to
privileged kernel components.
- Assume the presence of a user mode-exploitable vulnerability within kernel space.

## Implementation

- Cache probing
    - Map addresses into the same cache set
- Double page fault
- Address translation cache preloading

## Takeaway


## Questions


