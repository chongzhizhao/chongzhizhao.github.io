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
