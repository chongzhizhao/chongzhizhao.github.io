## Overview

Coherence makes cache invisible, while consistency makes shared memory virtually a
single module.

Processor cores are given 2 methods through coherence interface: 1) a *read-request* that
takes a memory location and returns a value; and 2) a *write-request* that takes a memory
location & a value and returns an acknowledgement.

Coherence invariants: single-writer-multiple-reader (SWMR) and data-value.

A memory consistency model (MC) defines permissable behaviors of multithreaded programs
with shared memory. It requires more than cache coherency and is also affected by the
reordering in the pipeline.

## Sequential Consistency (SC)

SC requires 1) that all cores insert their loads and stores into the global memory order
respecting their program order and 2) that every load gets its value from the last store
before it to the same address.

2 operations conflict if they are to the same address and at least one of them is a store.

SC dictates the order in which loads and stores get applied to coherent memory, but not the
order of coherence activity.

Synchronization requires atomic operations. It involves instructions that perform a "read-modify-write"
(RMW).

SC can be compared with database serializability.

## Total Store Order (TSO)

A store enters the write buffer when it commits and exits when the block is in the cache in
a read-write coherence state. TSO makes write buffer architecturally invisible while SC cannot.
It does so by omitting the Store -> Load constraint, which allows each core to use a write buffer.
Note that Store -> Store constraint requires the write buffer to be FIFO.

The value of a load is the value of the last store to the same address that is either a) before
it in memory order or b) before it in program order. Scenario b) take precedence, implying that
write buffer bypassing overrides the rest of the memory system.

FENCEs enforce program order onto memory order. If the programmer wants a store and a subsequent
load to be ordered, he must put a FENCE in between. Under TSO, a simple implementation of FENCE
may be draining the write buffer when executed and not permitting subsequent loads to execute
until it has committed.

The store queue holds uncommitted stores and the write buffer holds committed stores.

TSO write buffers are logically private to each thread context. Therefore, in multithreading,
one thread context shall never bypass from the write buffer of another thread context. This
is important for SMT/hyperthreading.

The atomic RMW effectively drains the write buffer before its load can be performed. Furthermore,
the load requires read-write coherence permissions. Lastly, to guarantee atomicity, the cache
controller may not relinquish coherence permission to the block between the load and the store.
