# Download
https://github.com/awakened1712/android_kernel_oneplus_sm8350_build/actions
# Kernel Features
- Built with GCC + Graphite + LTO + PGO
- Built-in kernel modules for better optimization with LTO
- Backport upstream Multi-gen LRU to optimize page reclaim and performance under memory pressure
- Backport entire RCU subsystem to Linux 6.0
- Lazy RCU which should result in power-savings while the device is lightly-loaded or idling
- Backport EEVDF Scheduler (Earliest Eligible Virtual Deadline First) in favor of CFS
- Disable unused touchscreen and keyboard drivers
- Disable tracing, statistics and various debugs
- Use power efficient workqueues
- Relax kernel wakelocks
- Backport upstream mremap
- Allocate small objects on stack instead of heap to reduce overhead
- Import latest version of Cortex strings' functions
- Disable kernel hardening for faster syscall performance

# Benchmarks
Callbench:
```
clock_gettime: ..........
    syscall:	87 ns
    libc:	33 ns

read file: ..........
    mmap:	7688 ns
    read:	4159 ns

* Eva:

clock_gettime: ..........
    syscall:	129 ns
    libc:	33 ns

read file: ..........
    mmap:	8593 ns
    read:	4369 ns

* BlueSpark:

clock_gettime: ..........
    syscall:	139 ns
    libc:	36 ns

read file: ..........
    mmap:	8876 ns
    read:	4571 ns
````
