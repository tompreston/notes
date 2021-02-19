# QNX
Command documentation:

    use
    use top
    use ls

Some useful commands:

    pidin

# Basics
- [procnto](http://www.qnx.com/developers/docs/7.0.0/index.html#com.qnx.doc.neutrino.utilities/topic/p/procnto.html) microkernel and process manager
- [tracelogger](http://www.qnx.com/developers/docs/7.0.0/#com.qnx.doc.neutrino.utilities/topic/t/tracelogger.html) logs procnto [events](https://www.qnx.com/developers/docs/6.5.0SP1.update/com.qnx.doc.instr_en_instr/events.html)
    The kernel events (kev) end up in `/dev/shmem/tracebuffer.kev`
- SAT stands for System Analysis Toolkit http://www.qnx.com/developers/docs/qnxcar2/index.jsp?topic=%2Fcom.qnx.doc.sat.user_guide%2Ftopic%2Fintroduction_Why_needed.html
- [on](http://www.qnx.com/developers/docs/6.5.0SP1.update/com.qnx.doc.neutrino_utilities/o/on.html) to set priority and background tasks (or `qon`)

# No uptime present
The uptime program reads /proc/uptime. If neither of these are present, try:

    [ICAS3-HOST]# pidin times | head -1 && pidin times | grep procnto
     pid name                   sid  start time   utime  stime cutime cstime
       1 /procnto-smp-instr       1 Jan 01  1970 31m06s  0.959  0.040  0.000

