## Background

Find the paper [here](https://cacheoutattack.com/).

Fallout, RIDL, and ZombieLoad show that attackers can leak data in-transit through
buffers including LFB. Thus, Intel issued microcode updates that repurposed the
`verw` instruction to overwrite the buffers. The OS is responsible to issue `verw` upon
every context switch.

## Attack Model

The attacker is an unprivileged user. The victim is an Intel-based system that is
fully patched against Meltdown, Foreshadow, and MDS in hardware and software.

TSX is present and enabled. The Attacker can run on the same physical core as the
victim. When attacking SGX, assume a malicious OS capable of configuring the CPU
and scheduler, including re-enabling TSX, stopping and starting enclaves, and making
arbitrary calls to SGX's paging instructions as needed.

## Insights

As data is being evicted from L1, it is often transferred to certain buffers.

There is undocumented interaction between LFB and L1D.

## Approach

Variant 1 targets data modified by the victim's write operations.

Variant 2 targets data read but not modified by the victim.

TAA-NG is deployed to control the byte offset and thus leak the whole line.

## Results


## Takeaway

LFB services data from lower level memory. Eviction victims enter LFB after eviction.

## Questions

