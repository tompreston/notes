# Debugging ideas and techniques
This note is for debugging inspiration.

# General
- Reliably reproduce the bug
- Compare with know working
- Reduce differences and iterate
- Try to bisect the problem
- Automate `git bisect` with tests

# Userland
- strace -ff -tt -yy -o foo.trace. ./foo
- strace -ff -tt -yy -x -e read=all -e write=all -o foo.trace. ./foo
- strace -i -k
- dstat, to look at IO usage
- opensnoop (TODO look into this), github.com/iovisor/bcc
- netstat -tunapl (tunaplease!) to see open ports https://writing.natwelch.com/post/581
- netstat -anpW (tunaplease doesn't show UNIX Domain Sockets)
- See perf notes
- ltrace (deprecated I think, use perf instead)
- ldd, `LD_TRACE_LOADED_OBJECTS=1`, or check running process maps /proc/$pid/maps
- Inject custom (debug) libraries with `LD_LIBRARY_PATH` or `LD_PRELOAD`
- If `LD_LIBRARY_PATH` doesn't work, add to /etc/ld.so.conf and run `ldconfig`
- `SEGFAULT_SIGNALS=all LD_PRELOAD=/lib/lib64/libSegFault.so ./foo` [0] [1]
- man 7 signals
- objdump -D -S foo | less
- readelf -d libbar.so
- coredump
    - `ulimit -a unlimited`
    - `ulimit -c unlimited`
    - `ulimit -H -c unlimited; ulimit -S -c unlimited` (embedded)
    - `sysctl -w kernel.core_pattern=/tmp/core-%e.%p.%h.%t`
        - sets /proc/sys/kernel/core_pattern
    - Or if using systemd, try coredumpctl
- gcc -g
- gdb
- valgrind
- Replace RO files with `mount --bind`, replace with a shell script to add logging


# Network and I/O specific
- Are we seeing lots of interrupts in `vmstat 1` or /proc/{interrupts,softirqs}
- dstat
- `netstat -ap`
- `netstat -tunapl`
- ngrep -d any metafilter, http://metafilter.com
- tcpdump port 8997 -w service.pcap
- wireshark

# Kernel specific
- dmesg
- dump_stack()
- current->comm,pid, CPU etc
- strace
- cat /sys/kernel/debug/regmap/device/registers
- kernel can't find working /sbin/init.../bin/sh, then try setting
  `init=/bin/sh`, it will give you a backtrace (maybe libs are broke)
- Set kernel command line
- grep term /proc/kallsyms
- ftrace, /sys/kernel/debug/tracing/, enable trace events for some time, then check trace_pipe

[0] https://www.marcusfolkesson.se/blog/libsegfault/
[1] https://sourceware.org/git/?p=glibc.git;a=blob;f=debug/segfault.c;hb=HEAD
