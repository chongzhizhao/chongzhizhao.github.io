## Overview

Coherence makes cache invisible, while consistency makes shared memory virtually a
single module.

Processor cores are given 2 methods through coherence interface: 1) a *read-request* that
takes a memory location and returns a value; and 2) a *write-request* that takes a memory
location & a value and returns an acknowledgement.

Coherence invariants: single-writer-multiple-reader (SWMR) and data-value.
