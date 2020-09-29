# Processes, POSIX, Linux etc
Some shortcuts for inspecting processes.

Print real-time priorities (ignore non-RT):

    ps ax -L -o comm,pid,tid,rtprio | grep -v " -"
