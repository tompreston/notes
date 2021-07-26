# Perf Performance Monitoring
See also:
* https://www.brendangregg.com/linuxperf.html
* https://github.com/sysstat/sysstat
* https://pcp.io/index.html
* Using Perf on ARM Platforms, Linaro
  https://s3.amazonaws.com/connect.linaro.org/yvr18/presentations/yvr18-416.pdf
  https://s3.amazonaws.com/connect.linaro.org/yvr18/videos/yvr18-416.mp4

# Basic usage
See available counters:

    perf list

Free-run to display counters of ls:

    perf stat ls

Free-run to display counters of gnome-terminal-server over 5 seconds:

    perf stat -p $(pidof gnome-terminal-server) -- sleep 5

Or top functions:

    perf top

# Recording
Record PID 375 for 10 seconds:

    perf record -F 1000 -p 375 -g -- sleep 10

Print a plaintext report:

    perf report -n --stdio > /tmp/trace.txt

Or use the data to generate a flamegraph:

    perf script > script.perf
    git clone https://github.com/brendangregg/FlameGraph.git
    cat script.perf | FlameGraph/stackcollapse-perf.pl > out.perf-folded
    FlameGraph/flamegraph.pl out.perf-folded > pid375-flamegraph.svg

Record system-wide backtraces for all syscalls. Eg. Show me all functions who
called `epoll_create1()` in the next 60 seconds:

    perf record -e syscalls:sys_enter_epoll_create1 -g -a sleep 60
    perf script

You can then write awk scripts to parse this and figure out who is calling it
the most often, then try to optimise there.

# strace
We can get some statistics from strace. Prints on kill:

    root@8x96autogvmquin:~# strace -c -p 375
    strace: Process 375 attached
    ^Cstrace: Process 375 detached
    % time     seconds  usecs/call     calls    errors syscall
    ------ ----------- ----------- --------- --------- ----------------
     95.88    0.020000        1333        15           epoll_pwait
      3.39    0.000707           2       294           epoll_ctl
      0.73    0.000152          10        15           close
      0.00    0.000000           0        15           epoll_create1
      0.00    0.000000           0         8           ioctl
      0.00    0.000000           0         7           read
      0.00    0.000000           0         8           write
      0.00    0.000000           0         7           sendto
      0.00    0.000000           0        24           recvfrom
    ------ ----------- ----------- --------- --------- ----------------
    100.00    0.020859                   393           total

Here something is using epoll stuff waaaaay too much.
