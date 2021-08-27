# Sensible Hardware Configurations

The default configuration of gem5 is not always sensible or realistic, which makes it
necessary to modify it to arrive at meaningful conclusions.

| Group | Parameter | File path | Corresponding variable | Default value | Sensible value(s) |
| :---: | :---: | :---: | :---: | :---: | :---: |
| CPU | | | | | |
| CPU | | | | | |
| Cache | L1 assoc | configs/common/Caches.py | L1Cache.assoc | 2 | 8 |
| Cache | L1 tag latency | configs/common/Caches.py | L1Cache.tag\_latency | 2 | 1 |
| Cache | L1 data latency | configs/common/Caches.py | L1Cache.data\_latency | 2 | 1 |
| Cache | L1 response latency | configs/common/Caches.py | L1Cache.response\_latency | 2 | 1 |
| Cache | L1 MSHRs | configs/common/Caches.py | L1Cache.mshrs | 4 | 128 |
| Cache | L1 targets per MSHR | configs/common/Caches.py | L1Cache.tgts\_per\_mshr | 16 | |
| Cache | L1 write buffers | configs/common/Caches.py | L1Cache.write\_buffers | undefined | 56 |
| Cache | L2 assoc | configs/common/Caches.py | L2Cache.assoc | 8 | 4 |
| Cache | L2 tag latency | configs/common/Caches.py | L2Cache.tag\_latency | 20 | 14 |
| Cache | L2 data latency | configs/common/Caches.py | L2Cache.data\_latency | 20 | 14 |
| Cache | L2 response latency | configs/common/Caches.py | L2Cache.response\_latency | 20 | 1 |
| Cache | L2 MSHRs | configs/common/Caches.py | L2Cache.mshrs | 20 | 256 |
| Cache | L2 targets per MSHR | configs/common/Caches.py | L2Cache.tgts\_per\_mshr | 12 | 16 |
| Cache | L2 write buffers | configs/common/Caches.py | L2Cache.write\_buffers | 8 | 256 |
| Cache | L3 assoc | configs/common/Caches.py | L3Cache.assoc | undefined | 16 |
| Cache | L3 tag latency | configs/common/Caches.py | L3Cache.tag\_latency | undefined | 44 |
| Cache | L3 data latency | configs/common/Caches.py | L3Cache.data\_latency | undefined | 44 |
| Cache | L3 response latency | configs/common/Caches.py | L3Cache.response\_latency | undefined | 1 |
| Cache | L3 MSHRs | configs/common/Caches.py | L3Cache.mshrs | undefined | 256 |
| Cache | L3 targets per MSHR | configs/common/Caches.py | L3Cache.tgts\_per\_mshr | undefined | 16 |
| Cache | L3 write buffers | configs/common/Caches.py | L3Cache.write\_buffers | undefined | 256 |
| Cache | | | | | |
| TLB | | | | | |
| TLB | | | | | |

Configuration of Intel Skylake microarchitecture can be found [here](https://www.7-cpu.com/cpu/Skylake.html).
