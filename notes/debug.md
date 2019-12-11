# Debugging ideas and techniques
This note is for debugging inspiration.

# General
- Reliably reproduce the bug
- Compare with know working
- Reduce differences and iterate
- Try to bisect the problem
- Automate `git bisect` with tests

# Userland
- strace -ff -tt -o foo.trace. ./foo
- ltrace
- gcc -g
- SEGFAULT_SIGNALS=ill LD_PRELOAD=/lib/lib64/libSegFault.so ./foo [0] [1]
- man 7 signals
- objdump -D -S foo | less
- gdb
- valgrind
- `mount --bind` over files to replace and/or log

# Kernel specific
- dmesg
- dump_stack()
- current->comm,pid, CPU etc
- strace
- cat /sys/kernel/debug/regmap/device/registers

[0] https://www.marcusfolkesson.se/blog/libsegfault/
[1] https://sourceware.org/git/?p=glibc.git;a=blob;f=debug/segfault.c;hb=HEAD
