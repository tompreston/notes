# LTTng
* https://lttng.org/docs/v2.12/

Read the docs for comprehensive info, this is just a cheat sheet of command
syntax.

## Kernel Tracing Quickstart

    lttng create my-kernel-session --output=/tmp/my-kernel-trace

    lttng list --kernel
    lttng list --kernel --syscall

    lttng enable-event --kernel sched_switch,sched_process_fork
    lttng enable-event --kernel --syscall open,close

    lttng enable-event --kernel --all

    lttng start

Do some stuff:

    lttng destroy

Track single processes:

    lttng enable-event --kernel --all --syscall
    lttng track --kernel --pid=2345
    lttng start
