## Emergence

A detailed timeline can be found [here](https://mdsattacks.com/). RIDL
was reported to Intel in 2018, prompting Intel to issue microcode updates.
The story from Intel's perspective is [here](https://software.intel.com/content/www/us/en/develop/articles/software-security-guidance/technical-documentation/intel-analysis-microarchitectural-data-sampling.html).
The response from Intel was to release `MD_CLEAR` functionality. On processors
that enumerate `MD_CLEAR`, `verw` or `L1D_FLUSH` should be used to cause the
processor to overwrite the affected buffers.

## Mechanisms

RIDL can exploit Line Fill Buffers and Load Ports. LFB implements multiple
MSHRs to enable a non-blocking cache.

Fallout leaks data from Store Buffers by forwarding a store value to a
faulting or assisting load.

ZombieLoad's authors deduce that the leakage sources are not only limited to
LFB but possibly including the load buffer. LFB serves as an interface to other caches
and the main memory and keeps track of outstanding loads. Memory accesses to
uncacheable memory regions, and non-temporal moves all go through the LFB.
